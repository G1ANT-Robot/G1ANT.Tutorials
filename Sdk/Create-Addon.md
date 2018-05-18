
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
9. Do the same with **G1ANT.Addon.AddonName.Tests** project (repeat steps 1..8)

You're ready.
