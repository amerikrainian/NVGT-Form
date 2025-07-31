# NVGT-Form

Rewrite of the old NVGT form

This is still a work in progress, but you can do as follows:

```nvgt
#include "form/form.nvgt"

void button_clicked(Event@ e) {
    speak("Button was clicked!", true);
}

Window@ main_window;  // Global so exit button can access it

void exit_button_clicked(Event@ e) {
    main_window.close();
}

void main() {
    @main_window = Window("Test Window");

    main_window.add_control(Button("Click Me", button_clicked));
    main_window.add_control(Button("Another Button", button_clicked));
    main_window.add_control(Button("Exit", exit_button_clicked));

    main_window.run();
}
```
