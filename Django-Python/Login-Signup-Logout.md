# Django Authentication

This repository contains the basic setup for user authentication (Signup, Login, Logout) in a Django project.

## Settings

```python
add in setting file 
LOGIN_URL = "/authe/login/"  # Redirect here if login is required
LOGIN_REDIRECT_URL = "/authe/home/"  # Redirect here after successful login
LOGOUT_REDIRECT_URL = "/authe/login/"  # Redirect here after logout
SESSION_ENGINE = "django.contrib.sessions.backends.db"



from django.shortcuts import render, redirect
from django.contrib.auth.models import User
from django.contrib.auth import authenticate, login, logout
from django.contrib.auth.decorators import login_required
from django.contrib import messages


# Signup View


def signup_view(request):
    if request.method == "POST":
        username = request.POST.get("username")
        email = request.POST.get("email")
        password = request.POST.get("password")
        confirm_password = request.POST.get("confirm_password")

        if password != confirm_password:
            messages.error(request, "Passwords do not match.")
            return redirect("signup")

        if User.objects.filter(username=username).exists():
            messages.error(request, "Username already taken.")
            return redirect("signup")

        if User.objects.filter(email=email).exists():
            messages.error(request, "Email already registered.")
            return redirect("signup")

        user = User.objects.create_user(username=username, email=email, password=password)
        user.save()
        messages.success(request, "Signup successful! Please log in.")
        return redirect("login")

    return render(request, "authSession/signup.html")


# Login View

def login_view(request):
    if request.method == "POST":
        username = request.POST.get("username")
        password = request.POST.get("password")

        user = authenticate(request, username=username, password=password)

        if user is not None:
            login(request, user)
            messages.success(request, "Login successful!")
            return redirect("home")
        else:
            messages.error(request, "Invalid username or password.")
            return redirect("login")

    return render(request, "authSession/login.html")


# Logout View
def logout_view(request):
    logout(request)
    messages.success(request, "You have been logged out.")
    return redirect("login")




# Home View (Protected)
@login_required
def home_view(request):
    return render(request, "authSession/home.html")

