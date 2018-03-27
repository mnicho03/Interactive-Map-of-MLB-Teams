# Interactive-Map-of-MLB-Teams
Utilizes the Leaflet Library
Major League Baseball Teams by Confe
rence Using Leaflet
Michael Nichols

3/27/2018

'''{r}
library(leaflet)
MLB_TeamInfo <- read.csv("Baseball_team-locationDeets.csv", header = TRUE)
conferencepal <- colorFactor(c("red", "blue"), MLB_TeamInfo$Conference) 


MLB_TeamInfo %>%
        leaflet() %>%
        addTiles() %>%
        addCircleMarkers(radius = 15,
                         fillColor = ~conferencepal(Conference),
                         fillOpacity = .25,
                         popup = paste("Team:", MLB_TeamInfo$Team, "<br>",
                                 "Location:", MLB_TeamInfo$City, "<br>",
                                 "Stadium:", MLB_TeamInfo$Stadium)) %>%
        addLegend("topright", pal = conferencepal, values = ~Conference, title = "MLB Conference Split")
'''
