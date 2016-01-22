# Local build and preview #
Open Publishing allows you to build your content locally to detect any potential error (like broken links), as well as preview your content locally for validation. Both operations run on [msbuild](https://msdn.microsoft.com/en-us/library/dd393574.aspx) commands. 

## Local build ##
1. Clone your repo to your local machine. You can use Visual Studio, [GitHub Desktop](https://desktop.github.com/).
	- From Visual Studio, right-click on the cloned repo and click on **Open command prompt**.
	- From GitHub Desktop, right-click on the repo and click on **Open in Git Shell**.
2. Run the `msbuild` under the root of the repo. 
3. Look at the report and fix any errors that you might have. Run `msbuild` again to validate you are error free. 

## Local preview ##
Once you do not have any errors on the content, you can run a local preview to validate the content and TOC look as you expect. This steps assumes you have cloned your repo already to your local machine.

1. Run `msbuild /t:serve` under the root of the repo.
2. Open `http://localhost:8000` in your browser.
3. Another command prompt window will appear, indicating that the local web site is being generated.

Note that any changes that you make after this point, are not going to be reflected in the local web site. You will need to close the command prompt window that popped up and run `msbuild /t:serve` again.



