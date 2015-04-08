# xyz
R related
 read.csv("\\\\ARLMSSAN01\\ListTech$\\indrajit_patil\\Indra R work\\Punit\\tagging\\unspsc_modified.csv", header=T)
tags <- unique(tagsFile$Level.4.Description)
temp <- data.frame()
for(i in 1:length(tags)){
  tagWord <- tags[i]
  pattern1 <- paste("\\b", tagWord, "\\b", sep="")
    
  
  ind <- grep(pattern1, data$Keywords, ignore.case = T, value=F)
    if(length(ind)>0){
      
      for(k in ind){
        
        word <- data$Keywords[k]
        qualifier1 <- gsub(paste(tagWord, ".*", sep=""), "", word, ignore.case = T)
        qualifier2 <- gsub(paste(".*",tagWord, sep=""), "", word, ignore.case = T)
        final <- cbind(i, qualifier1, tagWord, qualifier2, k)
