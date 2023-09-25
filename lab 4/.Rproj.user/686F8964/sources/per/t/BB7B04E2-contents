#
# This is the user-interface definition of a Shiny web application. You can
# run the application by clicking 'Run App' above.
#
# Find out more about building applications with Shiny here:
#
#    http://shiny.rstudio.com/
#

library(shiny)
library(ggplot2)
library(readr)


heroes_data <- read_csv("heroes_information.csv")

# Define UI for application that draws a histogram
shinyUI(fluidPage(

  titlePanel("Heroes Dashboard"),
  sidebarLayout(
    sidebarPanel(
      selectInput("publisher", "Select Publisher", choices = unique(heroes_data$Publisher), selected = NULL),
      textInput("hero_name", "Search Hero by Name"),
      textOutput("suma")
    ),
    mainPanel(
      tabsetPanel(
        tabPanel("Table", 
                 dataTableOutput("table")),
        tabPanel("Graph", plotOutput("plot", click =  "Click"), textOutput("text"))
        
      )
    )
  )
)
)
