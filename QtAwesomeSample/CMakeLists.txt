add_executable(QtAwesomeSample
    "main.cpp"
)

target_link_libraries(QtAwesomeSample
  PRIVATE
    QtAwesome
    Qt5::Widgets
)