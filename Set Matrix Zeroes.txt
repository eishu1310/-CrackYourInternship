class Solution:
    def setZeroes(self, mat: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        rows = len(mat)
        cols = len(mat[0])
        fcol = False
        frow = False

        # Check if there is a zero in first column, set fcol to True.
        for i in range(rows):
            if mat[i][0] == 0:
                fcol = True

        # Check if there is a zero in first row, set frow to True.
        for i in range(cols):
            if mat[0][i] == 0:
                frow = True

        # Check row elements (by ignoring first row and first column). If zero is found,
        # set corresponding row's and column's first element to zero.
        for i in range(1, rows):
            for j in range(1, cols):
                if mat[i][j] == 0:
                    mat[0][j] = mat[i][0] = 0

        # Check every row's first element starting from second row.
        # Set complete row to zero if zero is found.
        for i in range(1, rows):
            if mat[i][0] == 0:
                for j in range(1, cols):
                    mat[i][j] = 0

        # Check every column's first element starting from second column.
        # Set complete column to zero if zero is found.
        for j in range(1, cols):
            if mat[0][j] == 0:
                for i in range(1, rows):
                    mat[i][j] = 0

        # If fcol is true, set first column to zero.
        if fcol:
            for i in range(rows):
                mat[i][0] = 0

        # If frow is true, set first row to zero.
        if frow:
            for j in range(cols):
                mat[0][j] = 0