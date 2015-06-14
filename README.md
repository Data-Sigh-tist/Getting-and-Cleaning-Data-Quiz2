# Getting-and-Cleaning-Data-Quiz2
# Question 1

# Solution:

library(httr)
require(httpuv)
require(jsonlite)

myapp<- oauth_app("QZ_1","5028c8bff0156af5b62d",secret="a908d4d1155c6686638eed02008675b0fba42840")
github_token <- oauth2.0_token(oauth_endpoints("github"), myapp)
req <- GET("https://api.github.com/users/jtleek/repos", access_token="025810f0f1ee7413201e468c2f1c53bf9615d606")

# In the top right corner of any page, click your profile photo, then click Settings.

# Personal access tokensIn the user settings sidebar, click Personal access tokens.

# Generate new token buttonClick Generate new token.

# Token description fieldGive your token a descriptive name.
# Selecting token scopesSelect the scopes you wish to grant to this token. The default scopes allow you to interact with public and private repositories, user data, and gists.
# Generate token buttonClick Generate token.

stop_for_status(req)

c <- content(req)
json <- jsonlite::fromJSON(toJSON(c))
json[which(json$name == "datasharing"),]$created_at

