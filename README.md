import numpy as np

# Seed for reproducibility
np.random.seed(0)

# Create array
array = np.random.randint(1, 51, size=(5, 4))
print("Original Array:\n", array)


# Extract the Anti-Diagonal Elements 
anti_diagonal = [array[i, -i-1] for i in range(min(array.shape))]
print("Anti-diagonal Elements:", anti_diagonal)

max_in_rows = np.max(array, axis=1)
print("Maximum value in each row:", max_in_rows)

mean_value = np.mean(array)
filtered_array = array[array <= mean_value]
print(f"Mean of the array: {mean_value:.2f}")
print("Elements less than or equal to the mean:", filtered_array)

def numpy_boundary_traversal(matrix):
    rows, cols = matrix.shape
    boundary_elements = []

    # Top row
    for j in range(cols):
        boundary_elements.append(matrix[0, j])
    
    # Right column (excluding first and last)
    for i in range(1, rows - 1):
        boundary_elements.append(matrix[i, cols - 1])
    
    # Bottom row (reversed)
    for j in reversed(range(cols)):
        boundary_elements.append(matrix[rows - 1, j])
    
    # Left column (excluding first and last)
    for i in reversed(range(1, rows - 1)):
        boundary_elements.append(matrix[i, 0])
    
    return boundary_elements

# Call function
boundary = numpy_boundary_traversal(array)
print("Boundary Traversal (Clockwise):", boundary)
