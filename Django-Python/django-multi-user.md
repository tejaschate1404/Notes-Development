from django.contrib.auth.models import AbstractUser
from django.db import models

class CustomUser(AbstractUser):
    ROLE_CHOICES = [
        ('admin', 'Admin'),
        ('employee', 'Employee'),
        ('hr', 'HR'),
        ('reference_person', 'Reference Person'),
    ]
    
    role = models.CharField(max_length=20, choices=ROLE_CHOICES, default='employee')

    def __str__(self):
        return f"{self.username} - {self.role}"



from django.urls import path
from .views import signup, login_view, logout_view, admin_dashboard, employee_dashboard, hr_dashboard, reference_person_dashboard

urlpatterns = [
    path('signup/', signup, name='signup'),
    path('login/', login_view, name='login'),
    path('logout/', logout_view, name='logout'),
    path('admin_dashboard/', admin_dashboard, name='admin_dashboard'),
    path('employee_dashboard/', employee_dashboard, name='employee_dashboard'),
    path('hr_dashboard/', hr_dashboard, name='hr_dashboard'),
    path('reference_person_dashboard/', reference_person_dashboard, name='reference_person_dashboard'),
]



from django.shortcuts import render, redirect
from django.http import HttpResponse
from django.contrib.auth import authenticate, login, logout
from django.contrib.auth.decorators import login_required
from django.contrib.auth.hashers import make_password
from .models import CustomUser
from .utils import role_required  # Import the decorator

def signup(request):
    if request.method == "POST":
        username = request.POST.get("username")
        email = request.POST.get("email")
        password = request.POST.get("password")
        role = request.POST.get("role")

        if CustomUser.objects.filter(username=username).exists():
            return render(request, "signup.html", {"error": "Username already exists."})

        user = CustomUser(username=username, email=email, role=role)
        user.password = make_password(password)
        user.save()

        login(request, user)
        return redirect_user_dashboard(user)

    return render(request, "signup.html")

def login_view(request):
    if request.method == "POST":
        username = request.POST.get("username")
        password = request.POST.get("password")
        
        user = authenticate(request, username=username, password=password)

        if user is not None:
            login(request, user)
            return redirect_user_dashboard(user)
        else:
            return render(request, "login.html", {"error": "Invalid username or password"})

    return render(request, "login.html")

def logout_view(request):
    logout(request)
    return redirect("login")

def redirect_user_dashboard(user):
    if user.role == 'admin':
        return redirect('admin_dashboard')
    elif user.role == 'employee':
        return redirect('employee_dashboard')
    elif user.role == 'hr':
        return redirect('hr_dashboard')
    elif user.role == 'reference_person':
        return redirect('reference_person_dashboard')

@login_required
@role_required(allowed_roles=["admin"])
def admin_dashboard(request):
    return render(request, 'dashboards/admin.html', {'user': request.user})


@login_required
@role_required(allowed_roles=["employee"])
def employee_dashboard(request):
    return render(request, 'dashboards/employee_dashboard.html', {'user': request.user})

@login_required
@role_required(allowed_roles=["hr"])
def hr_dashboard(request):
    return render(request, 'dashboards/hr_dashboard.html', {'user': request.user})

@login_required
@role_required(allowed_roles=["reference_person"])
def reference_person_dashboard(request):
    return render(request, 'dashboards/reference_person_dashboard.html', {'user': request.user})



utils

from django.shortcuts import redirect
from functools import wraps

def role_required(allowed_roles=[]):
    def decorator(view_func):
        @wraps(view_func)
        def wrapped_view(request, *args, **kwargs):
            if request.user.is_authenticated and request.user.role in allowed_roles:
                return view_func(request, *args, **kwargs)
            return redirect("login")  # Redirect unauthorized users
        return wrapped_view
    return decorator

