3rd question

    matrix = [
        [99, 114, 121, 112],
        [116, 111, 123, 105],
        [110, 109, 97, 116],
        [114, 105, 120, 125],
    ]
    def matrix2bytes(matrix):
        """ Converts a 4x4 matrix into a 16-byte array.  """
        return b''.join(bytes(row) for row in matrix)
    
    print(matrix2bytes(matrix))
