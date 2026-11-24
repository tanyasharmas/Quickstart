+++
date = '2026-11-22T16:15:30+11:00'
draft = false
title = 'How Did I Create a New Post'
+++

## Steps to create a new post

1. Add the new file to contents/posts folder


```
hugo new content/posts/myfirstblogpage.md
```


2. Write the content on the newly created file
    Here is the syntax guide for writing .md files
    https://www.markdownguide.org/basic-syntax/#ordered-lists

3. Save file


4. Run hugo server

```
hugo server -D
```

5. Stop server

```
Ctrl +C
```

6. Verify that your changes are showing up in the localhost

## Ready to commit the changes to git?


1. Check git status

    ```
    git status
    ```

2. Add documents to git staging
```
git add ...path/filename
```
3. Add commit
```
git commit -M "commit message goes here"
```

4. Push the updates to git

```
git push
```

5. Run the hugo server
```
hugo server
```
6. Verify that the github action has run
7. Reload github page to see the new version






