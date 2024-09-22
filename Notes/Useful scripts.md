# Copy files from current directory to another directory that match a pattern, but preserve relative structure.
```bash
#!/bin/bash

# Check for correct usage: the script requires exactly two arguments
if [ $# -ne 2 ]; then
    echo "Usage: $0 <pattern> <destination_directory>"
    exit 1
fi

# Assign arguments to variables for better readability
PATTERN=$1                # The pattern of files to search for (e.g., "*.txt")
DEST_DIR=$2              # The directory where matched files will be copied

# Create the destination directory if it doesn't exist
# -p: Create parent directories as needed; do not throw an error if the directory already exists
mkdir -p "$DEST_DIR"

# Find files matching the specified pattern in the current directory
# .: Start the search in the current directory
# -type f: Search only for files (not directories)
# -name "$PATTERN": Match files that fit the specified name pattern
find . -type f -name "$PATTERN" | while read -r FILE; do # -r don't escape characters
    # Get the relative path of the found file by removing the leading './'
    # This makes the path cleaner for copying
    REL_PATH="${FILE#./}"

    # Extract the directory path from the relative file path
    # dirname: Get the directory portion of the file path
    TARGET_DIR="$(dirname "$REL_PATH")"

    # Create the corresponding directory structure in the destination directory
    # -p: Create parent directories as needed; do not throw an error if the directory already exists
    mkdir -p "$DEST_DIR/$TARGET_DIR"

    # Copy the file to the new destination while maintaining the directory structure
    # $FILE: The source file to copy
    # $DEST_DIR/$REL_PATH: The destination path where the file will be copied
    cp "$FILE" "$DEST_DIR/$REL_PATH"
done

# Print a message indicating the operation was successful
echo "Files matching '$PATTERN' have been copied to '$DEST_DIR'."

```