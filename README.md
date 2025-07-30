# NVGT-Form

Rewrite of the old NVGT form

This is still heavily in progress, but you can do as follows:

```nvgt
#include "form/form.nvgt"

void button_clicked(Event@ e) {
    speak("Button was clicked!", true);
}

Window@ mainWindow;  // Global so exit button can access it

void exit_button_clicked(Event@ e) {
    if (@mainWindow !is null) {
        mainWindow.close();
    }
}

void main() {
    @mainWindow = Window("Test Window");

    Panel@ buttonPanel = Panel("Button Group");

    Button@ btn1 = Button("Click Me");
    btn1.on_click.add(button_clicked);
    buttonPanel.add_child(btn1);

    Button@ btn2 = Button("Another Button");
    btn2.on_click.add(button_clicked);
    buttonPanel.add_child(btn2);

    Button@ exitBtn = Button("Exit");
    exitBtn.on_click.add(exit_button_clicked);
    buttonPanel.add_child(exitBtn);

    mainWindow.add_control(buttonPanel);

    mainWindow.run();

    speak("Window closed", true);
}
```
