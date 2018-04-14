## Stemming
Corpus comes with built-in support for the algorithmic stemmers provided by the Snowball Stemming Library, which supports the following languages: arabic (ar), danish (da), german (de), english (en), spanish (es), finnish (fi), french (fr), hungarian (hu), italian (it), dutch (nl), norwegian (no), portuguese (pt), romanian (ro), russian (ru), swedish (sv), tamil (ta), and turkish (tr). You can select one of these stemmers using either the full name of the language of the two-letter country code
```markdown
text <- "love loving lovingly loved lover lovely love"
text_tokens(text, stemmer = "en") # english stemmer
[[1]]
[1] "love"  "love"  "love"  "love"  "lover" "love"  "love" 
```
[editor on GitHub](https://github.com/akash5551/stress-detection-in-social-networks/edit/master/README.md) 
### Dictionary Stemmer
****
```markdown
```
```markdown
stemop<-function(dataset){
  require('plyr')
  require('corpus')
  #text stemming for live data
  url <- "http://www.lexiconista.com/Datasets/lemmatization-en.zip"
  tmp <- tempfile()
  download.file(url, tmp)
  # extract the contents
  con <- unz(tmp, "lemmatization-en.txt", encoding = "UTF-8")
  tab <- read.delim(con, header=FALSE, stringsAsFactors = FALSE)
  names(tab) <- c("stem", "term")
  head(tab)
  tab
  stem_list <- function(term) {
    i <- match(term, tab$term)
    if (is.na(i)) {
      stem <- term
    } else {
      stem <- tab$stem[[i]]
    }
    stem
  }
  dataset$tweet.<-laply(dataset$tweet.,function(text){
    x<-text_tokens(text, stemmer = stem_list) # english stemmer
    text<-paste(unlist(x), collapse = ' ')  
  })
  return(dataset)
}
nm<-read.csv('narendramodi.csv')
stemdataset<-stemop(nm)
nm$tweet.[264]
stemdataset$tweet.[264]
```
For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/akash5551/stress-detection-in-social-networks/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
