# Picture-Plagiat
Analis picture
# Code for Image Plagiarism Analyzer using image hashing
from imagehash import average_hash
from PIL import Image

def calculate_image_similarity(image_path1, image_path2, threshold=5):
    # Load the images
    image1 = Image.open(image_path1)
    image2 = Image.open(image_path2)

    # Calculate the average hash for each image
    hash1 = average_hash(image1)
    hash2 = average_hash(image2)

    # Calculate the Hamming distance between the hashes
    hamming_distance = hash1 - hash2

    # Check if the Hamming distance is below the threshold
    if hamming_distance < threshold:
        return True
    else:
        return False

# Example usage
image_path1 = "path/to/your/image1.jpg"
image_path2 = "path/to/your/image2.jpg"

if calculate_image_similarity(image_path1, image_path2):
    print("Plagiarism detected!")
else:
    print("No plagiarism found.")
