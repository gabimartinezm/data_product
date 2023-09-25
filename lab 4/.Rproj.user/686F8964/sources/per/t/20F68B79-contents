install.packages("shiny.router")
library(shiny.router)
library(shiny)
library(ggplot2)
library(readr)
library(plotly)
library(dplyr)


heroes_data <- read_csv("heroes_information.csv")

# Define server logic required to draw a histogram
shinyServer(function(input, output, session) {
  
  enableBookmarking("url")
  
  
  output$table <- renderDataTable({
    data <- heroes_data
    if(!is.null(input$publisher)) {
      data <- data[data$Publisher == input$publisher, ]
    }
    if(input$hero_name != "") {
      data <- data[data$name == input$hero_name,  ]
    }
    data
  })
  
  output$suma <- renderText({
    
    suma_filtro <- heroes_data[heroes_data$Publisher == input$publisher, ]
    
    suma_total <- nrow(suma_filtro)
    
    print(suma_total)
    
    paste0("Existen " , suma_total , " registros del editor: " ,  input$publisher)
  })
  
  output$plot <- renderPlot({
    plot(heroes_data$Height, heroes_data$Weight, pch = 19)
  })
  
  
  observeEvent(input$Click, {
    clicked_x <- input$Click$x
    clicked_y <- input$Click$y
    
    # Encuentra el registro correspondiente en 'data' basado en las coordenadas
    selected_record <- heroes_data[heroes_data$Height == clicked_x & heroes_data$Weight == clicked_y, ]
    
    # Muestra la información del registro
    output$text <- renderText({
      paste("Registro seleccionado:", selected_record)
    })
    
  #hola  
  })
  
  observe({
    param_value <- parseQueryString(session$clientData$url_search)$value
    
    
    if (!is.null(param_value) && param_value %in% heroes_data$Publisher) {
      updateSelectInput(session, "publisher", selected = param_value)
    }
    
    print(param_value)
    
    
  })
  
  
})
  
 
  
  
  



