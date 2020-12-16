# IDB_Notes
Notes from Introduction to Databases 2020. University of Edinburgh 3rd year. 

## Usage
1. Open 'IDB_All_Lecture_Notes.pdf'
2. Worship the holy gods of Pandoc.

## Contributing
Note: If you don't have the requirements but want to contribute, you can just do the first step and contact me
0. Requirements: markdown editor, bash, pandoc, latex engine 
1. Update the individial lecture markdown files
2. Run the following from the project root in order

```bash 
cat L*.md > IDB_All_Lecture_Notes.md
```
```bash 
pandoc IDB_All_Lecture_Notes.md -o IDB_All_Lecture_Notes.pdf --toc
```

## Todo's
- [ ] make a list of todo's
- [ ] write a bash script to automate contributing
