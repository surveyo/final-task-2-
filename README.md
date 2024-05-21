# final-task-2-
task_2_has_been_completed_successfully
import matplotlib.pyplot as plt


class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def translate(self, dx, dy):
        self.x += dx
        self.y += dy


def main():
    points = []
    with open("coordinate_file.csv", "r") as file:
        # Read and skip the header row (if present)
        first_line = file.readline().strip()
        if first_line:  # Check if there's a header line
            # Skip the header if it exists
            next(file)

        for line in file:
            x, y = line.strip().split(",")
            points.append(Point(float(x), float(y)))

    x_data = [point.x for point in points]
    y_data = [point.y for point in points]
    plt.scatter(x_data, y_data, label="Original Data")

    for point in points:
        point.translate(2, 1)

    x_data = [point.x for point in points]
    y_data = [point.y for point in points]
    plt.scatter(x_data, y_data, label="Translated Data", color="red")

    plt.xlabel("X-axis")
    plt.ylabel("Y-axis")
    plt.title("Scatter Plot")
    plt.legend()
    plt.show()


if __name__ == "__main__":
    main()
