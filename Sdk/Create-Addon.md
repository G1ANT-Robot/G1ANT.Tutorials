
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

3. Right click on the solution name
4. Click **Add -> New Project...**
5. Enter test project name in format **G1ANT.Addon.AddonName.Tests** (for example ```G1ANT.Addon.GoogleDocs.Tests```)
6. Choose project type as **Unit Test Project (.NET Framework) - Visual C#**
7. Choose **.NET Framework 4.6.1**
8. Delete **UnitTest1.cs** file

You're ready.

----------------------------

## (Optionally) Step 3 - Copy all files from
