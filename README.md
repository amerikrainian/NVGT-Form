# NVGT-Form

Rewrite of the old NVGT form

This is still a work in progress, but you can do as follows:

```nvgt
#include "form/form.nvgt"

Window@ main_window;  // Global so exit button can access it

void button_clicked(Event@ e) {
    speak("Button was clicked!", true);
}

void checkbox_changed(Event@ e) {
    speak("And the world was toggled...", false);
}

void list_item_selected(Event@ e) {
    ListEvent@ list_event = cast<ListEvent@>(e);
    speak("Selected: " + list_event.item.get_text(), true);
}

void exit_button_clicked(Event@ e) {
    main_window.close();
}

void main() {
    @main_window = Window("Test Window");

    main_window.add_control(Button("Click Me", button_clicked));
    main_window.add_control(Checkbox("Enable notifications", false, checkbox_changed));
    
    // List with position announcements
    main_window.add_control(
        List("Favorite colors", true, list_item_selected)
            .add("Red")
            .add("Green") 
            .add("Blue")
            .add("Yellow")
    );
    
    // List without position announcements
    main_window.add_control(
        List("Recent files", false)
            .add("document.txt")
            .add("image.png")
            .add("data.csv")
    );
    
    main_window.add_control(Button("Exit", exit_button_clicked));

    main_window.run();
}
```
