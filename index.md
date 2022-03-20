library(magick)

drake_eww <- image_read("https://static.hiphopdx.com/2015/10/drake-hotline-bling-jacket-moncler.png") %>%
  image_scale(500)

drake_mmm <- image_read("https://i.imgflip.com/4wpsm3.jpg") %>%
  image_scale(500)

eww_text <- image_blank(width = 500, 
                          height = 500, 
                          color = "#000000") %>%
  image_annotate(text = "Stats20X",
                 color = "#FFFFFF",
                 size = 80,
                 font = "Impact",
                 gravity = "center")

mmm_text <- image_blank(width = 500, 
                         height = 505, 
                         color = "#000000") %>%
  image_annotate(text = "Stats220",
                 color = "#FFFFFF",
                 size = 80,
                 font = "Impact",
                 gravity = "center")


first_row <- c(drake_eww, eww_text) %>%
  image_append()

second_row <- c(drake_mmm, mmm_text) %>%
  image_append()


meme <- c(first_row, second_row) %>%
  image_append(stack = TRUE) %>%
  image_scale(600)
meme

image_write(meme, "my_meme.png")
