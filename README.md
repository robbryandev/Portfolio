# Portfolio

## Commands used to auto set-up gh-pages for projects:
### Clone all repos
```
for r in https://github.com/robbryandev/my-first-webpage-final.git https://github.com/robbryandev/cookie-recipe.git https://github.com/robbryandev/pet-homepage.git https://github.com/robbryandev/branch-test.git https://github.com/robbryandev/resort-website.git https://github.com/robbryandev/cupcake-shop.git https://github.com/robbryandev/resume-div-span https://github.com/robbryandev/Interior-Decorator-div-test.git https://github.com/robbryandev/blog-website.git https://github.com/robbryandev/animal-shelter.git; do git clone $r; done;
```

### Publish gh-pages branches
#### Breakdown
1. Get all file / directory entries in the current directory (Only directories are in the current directory)
2. Filter out the current directory from the selection
3. Remove the ./ in the path so it only prints the name
4. Split path names
5. Pipe path names into a command chain
6. Run command chain on each path name
  Chain:
    1. Change directory to the repository path
    2. Create a gh-pages branch
    3. Switch to the gh-pages branch
    4. Push the gh-pages branch to a new remote gh-pages branch on github
    5. Print gh-pages url
    6. Change directory back to the previous directory

#### Command
```
find -maxdepth 1 | grep ./ | sed 's/.\///g' | awk {"print $1"} | xargs -i  sh -c "cd ./{} && git branch gh-pages && git checkout gh-pages && git push origin gh-pages && echo https://robbryandev.github.io/{} && cd .."
```