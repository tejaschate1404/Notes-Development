<h1>Commands of Github</h1>

<ol>
  <li><p><strong>git clone <<url>url> </strong> to pull all code from github we have to use this command and url https as given in github </p></li>
  <li><p><strong>git status </strong>  </p>
  <ul>
    <li>show the status of branch</li>
    <li>There are 4 types of status available in </li>
     <li>1} <strong>Modified</strong> changes will be done in file</li>
     <li>2} <strong>Untracked</strong> git can't track the changes</li>
     <li>3} <strong>staged</strong> by using git add command change the status to staged. and also files are ready to commite </li>
     <li>4} <strong>Unmodified</strong> by using git commite the file will move to unmodified stage </li>
  </ul>
  </li>
     <li><p><strong>git add file_Name </strong> </p>
    <p> git add is an stage of before commite. this will be a verification stage. after using git add command project file will be show staged in git status </p>
     <p><strong>git add .</strong> ===== is used for staged all the changes in all file</p>
     </li>
     <li><p><strong>git commite -m "Some Message"  </strong> ========   </p>
    <p>for traking our recore git can not use staged staged they need proper command or message so commite will be done</p>
     </li>
</ol>

<ol>
  <li><strong>git push origin main</strong> origin is copy and main is branch name</li>
</ol>


<hr>
<hr>
<h3>How to upload new files on github with vscode</h3>
<ol>
  <li><strong>git init</strong> =========  initialize the git </li>
   <li><strong>git add .</strong> =========  files go on staged stage </li>
   <li><strong>git commite -m "some messge"</strong> =========  Commite the change </li>
   <li>Then we have to make repositery on github website</li>
   <li><strong>git remote add origin <<url>url></strong> =========  set the origine of repo </li>
   <li><strong>git remote -v</strong> =========  check the origin is set </li>
   <li><strong>git branch</strong> =========  check branch </li>
   <li><strong>git branch -M main</strong> =========  to change our branch name to main because today github use main branch as default branch </li>
   <li><strong>git push origin main </strong> =========  push the code in github </li>
   <li><strong>git push -u origin main </strong> =========  to set we have to use main branch most of time so simple <strong> git push </strong> will push the code </li>
   
</ol>
