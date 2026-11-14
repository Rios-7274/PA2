cmake_minimum_required(VERSION 4.3)
project(cs210_pa2_starter)

set(CMAKE_CXX_STANDARD 14)

include_directories(cs210_pa2_starter)

add_executable(cs210_pa2_starter
        cs210_pa2_starter/Adventure.cpp
        cs210_pa2_starter/Adventure.h
        cs210_pa2_starter/Item.h
        cs210_pa2_starter/List.h
        cs210_pa2_starter/main.cpp
        cs210_pa2_starter/Moment.h
        cs210_pa2_starter/Node.h
        cs210_pa2_starter/Scene.h
        cs210_pa2_starter/StoryTree.h)

configure_file(cs210_pa2_starter/bee_movie.txt bee_movie.txt COPYONLY)
configure_file(cs210_pa2_starter/bad_story.txt bad_story.txt COPYONLY)
configure_file(cs210_pa2_starter/my_story.txt my_story.txt COPYONLY)
