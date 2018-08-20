**Display Counters in Bubbles Easily, 2.0**  
*By Toothless#7854*  
  
Here is an updated version of the Bubble Counter. This sets the counter's name as a variable so a) the user only needs to change one value to get the snippet to work, and b) sets up your alias to be modular, so other snippets such as ``{{mod_cc(counter, -1, True)}}`` can be added and work seemlessly.  
  
Replace ``counterName`` with the counter name. Make sure it is exactly the same as the counter name.  
  
``{{set("counter", "counterName")}} -f "{{counter}}|{{'◉'*get_cc(counter) + '〇'*(get_cc_max(counter)-get_cc(counter))}}"``