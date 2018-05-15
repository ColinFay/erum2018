# erum2018
"Building a package that lasts" — eRum 2018 workshop

## Program

+ 13h30- 14h00: [Introduction & Package init](chap1.pdf)

+ 14h00 - 14h30: [Functions and documentation](chap2.pdf)

+ 14h30 - 15h00: [Dependencies](chap3.pdf)

__Coffee Break: 15h - 15h30__ 

+ 15h30 - 16h00: [Optimisation](chap4.pdf)

+ 16h00 - 16h30: [Testing](chap5.pdf)

+ 16h30 - 16h45: [Continuous integration](chap6.pdf)

+ 16h45 - 17h00: [Conclusion](chap7.pdf)

## Functions for the workshop

### (if you're not planning on using your own)

```r
init_data_raw <- function(name = "devstuffs"){
  stop_if_not(name, is.character, "Please use a character vector")
  use_data_raw()
  
  new_file_path <- glue({here()}, "/data-raw/{name}.R")
  file.create(new_file_path)
  file.edit(new_file_path)
}

init_docs <- function(name = "Colin FAY"){
  stop_if_not(name, is.character, "Please use a character vector")
  use_mit_license(name)
  use_readme_rmd()
  use_news_md()
  use_testthat()
}

fill_desc <- function(name, Title, Description, repo){
  unlink("DESCRIPTION")
  my_desc <- description$new("!new")
  my_desc$set("Package", name)
  my_desc$set("Authors@R", "person('Colin', 'Fay', email = 'contact@colinfay.me', role = c('cre', 'aut'))")
  my_desc$del("Maintainer")
  my_desc$set_version("0.0.0.9000")
  my_desc$set(Title = Title)
  my_desc$set(Description = Description)
  my_desc$set("URL", glue("https://github.com/ColinFay/{repo}"))
  my_desc$set("BugReports", glue("https://github.com/ColinFay/{repo}/issues"))
  my_desc$write(file = "DESCRIPTION")
}


fill_desc_generic <- function(name, Title, Description = "Here", repo,
                              first_name = "Colin",
                              last_name = "Fay",
                              github_user = "ColinFay",
                              email = "contact@colinfay.me",
                              role = "c('cre', 'aut')",
                              version = "0.0.0.9000"){
  unlink("DESCRIPTION")
  my_desc <- description$new("!new")
  my_desc$set("Package", name)
  my_desc$set("Authors@R",
              glue("person('{first_name}', '{last_name}', email = '{email}', role = {role}"))
  my_desc$del("Maintainer")
  my_desc$set_version(version)
  my_desc$set(Title = Title)
  my_desc$set(Description = Description)
  my_desc$set("URL", glue("https://github.com/{github_user}/{repo}"))
  my_desc$set("BugReports", glue("https://github.com/{github_user}/{repo}/issues"))
  my_desc$write(file = "DESCRIPTION")
}
```
