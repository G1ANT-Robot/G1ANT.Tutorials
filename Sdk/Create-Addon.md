
# How to create G1ANT Add-On

## Step 1 - Create Solution

1. Click **File -> New -> Project <Ctrl+Shift+N>**
2. Enter project name in format **G1ANT.Addon.AddonName** (for example ```G1ANT.Addon.GoogleDocs```)
3. Choose project type as **Class Library (.NET Framework) - Visual C#**
4. Choose **.NET Framework 4.6.1**
5. Check **Create directory for solution**
6. Check **Create new Git repository**
7. Attention - project name should be the same as solution name
8. Enter to the Solution explorer panel
9. Delete **Class1.cs** file (permanently)

## Step 2 - Create unit tests

1. Right click on the solution name
2. Click **Add -> New Project...**
3. Enter test project name in format **G1ANT.Addon.AddonName.Tests** (for example ```G1ANT.Addon.GoogleDocs.Tests```)
4. Choose project type as **Unit Test Project (.NET Framework) - Visual C#**
5. Choose **.NET Framework 4.6.1**
6. Delete **UnitTest1.cs** file

## Step 3 - Optional (if you have to copy files from old repository)

1. Go to old repository, select all files and folders to copy (except **bin**, **obj** and **ProjectName.csproj**)
2. Press **<Ctrl+C>** to copy all files to clipboard
3. Go to Solution Explorer and click project name  (for example ```G1ANT.Addon.GoogleDocs```)
4. Press **<Ctrl+V>**
5. Choose **Apply to all items** and click **Yes**
6. Click **File -> Close Solution**
7. Save changes -> click **Yes**
8. Copy old file **ProjectName.csproj** (for example ```G1ANT.Addon.GoogleDocs.csproj```) from old repository to the new repository outside the Visual Studio (by **Windows File Explorer**)
9. Reopen solution **G1ANT.Addon.AddonName**
9. Do the same with **G1ANT.Addon.AddonName.Tests** project (repeat steps 1..8)

## Step 4 - Optional (if you have to copy additional projects from old repository)

1. Right click on the solution name
2. Click **Add -> New Project...**
3. Enter project name (for example ```Watin.Core```)
4. Choose project type as **Unit Test Project (.NET Framework) - Visual C#**
5. Choose **.NET Framework 4.6.1**
6. Delete **Class1.cs** file
7. Go to old repository, select all files and folders to copy (except **bin**, **obj** and **ProjectName.csproj**)
8. Press **<Ctrl+C>** to copy all files to clipboard
9. Go to Solution Explorer and click project name  (for example ```G1ANT.Addon.GoogleDocs```)
10. Press **<Ctrl+V>**
11. Choose **Apply to all items** and click **Yes**
12. Click **File -> Close Solution**
13. Save changes -> click **Yes**
14. Copy old file **ProjectName.csproj** (for example ```G1ANT.Addon.GoogleDocs.csproj```) from old repository to the new repository outside the Visual Studio (by **Windows File Explorer**)
15. Reopen solution **G1ANT.Addon.AddonName**
16. Do the same with other additional projects (repeat steps 1..15)

## Step 5 - Optional (if you have to copy additional folders from old repository)

1. Right click on the solution name
2. Click **Add -> New Solution Folder...**
3. Enter solution directory and press **<Enter>**
4. Go to old folder, select all files to copy
2. Press **<Ctrl+C>** to copy all files to clipboard
3. Go to Solution Explorer and click additinonal folder name
4. Press **<Ctrl+V>**
5. Choose **Apply to all items** and click **Yes**

## Step 6 - Prepare Addon to work

1. Rename file **AddonNameAddon.cs** to **Addon.cs** in Visual Studio

## Step 7 - Push solution to GITHub

1. Right click on the solution name
2. Click **Commit**
3. Enter ```Init``` and press **Commit All** 
4. Click **Sync**
5. Click **Publish to GitHub**
6. Choose **G1ANT-Robot**
7. Uncheck **Private Repository**
8. Click **Publish**
9. Check the repository on the https://github.com/G1ANT-Robot/G1ANT.Addon.AddonName
