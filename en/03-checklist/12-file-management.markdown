## File Management: {#file-management .list-paragraph}

-   Do not pass user supplied data directly to any dynamic include
    > function

-   Require authentication before allowing a file to be uploaded

-   Limit the type of files that can be uploaded to only those types
    > that are needed for business purposes

-   Validate uploaded files are the expected type by checking file
    > headers. Checking for file type by extension alone is not
    > sufficient

-   Do not save files in the same web context as the application. Files
    > should either go to the content server or in the database.

-   Prevent or restrict the uploading of any file that may be
    > interpreted by the web server.

-   Turn off execution privileges on file upload directories

-   Implement safe uploading in UNIX by mounting the targeted file
    > directory as a logical drive using the associated path or the
    > chrooted environment

-   When referencing existing files, use a white list of allowed file
    > names and types. Validate the value of the parameter being passed
    > and if it does not match one of the expected values, either reject
    > it or use a hard coded default file value for the content instead

-   Do not pass user supplied data into a dynamic redirect. If this must
    > be allowed, then the redirect should accept only validated,
    > relative path URLs

-   Do not pass directory or file paths, use index values mapped to
    > pre-defined list of paths

-   Never send the absolute file path to the client

-   Ensure application files and resources are read-only

-   Scan user uploaded files for viruses and malware
