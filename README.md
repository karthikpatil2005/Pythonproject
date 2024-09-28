# Pythonproject
import datetime

class Inspection:
    def __init__(self, date, type_of_inspection):
        self.date = date
        self.type_of_inspection = type_of_inspection

    def __str__(self):
        return f"Inspection Type: {self.type_of_inspection}, Date: {self.date.strftime('%Y-%m-%d')}"

class SafetyInspectionScheduler:
    def __init__(self):
        self.inspections = []

    def add_inspection(self, date, type_of_inspection):
        inspection = Inspection(date, type_of_inspection)
        self.inspections.append(inspection)
        print(f"Added: {inspection}")

    def view_inspections(self):
        if not self.inspections:
            print("No inspections scheduled.")
        else:
            print("Scheduled Inspections:")
            for inspection in self.inspections:
                print(inspection)

    def remove_inspection(self, date):
        for inspection in self.inspections:
            if inspection.date == date:
                self.inspections.remove(inspection)
                print(f"Removed: {inspection}")
                return
        print("No inspection found on this date.")

def main():
    scheduler = SafetyInspectionScheduler()

    while True:
        print("\nSafety Inspection Scheduler")
        print("1. Add Inspection")
        print("2. View Inspections")
        print("3. Remove Inspection")
        print("4. Exit")

        choice = input("Choose an option: ")

        if choice == '1':
            date_str = input("Enter inspection date (YYYY-MM-DD): ")
            date = datetime.datetime.strptime(date_str, '%Y-%m-%d')
            type_of_inspection = input("Enter type of inspection: ")
            scheduler.add_inspection(date, type_of_inspection)
        
        elif choice == '2':
            scheduler.view_inspections()

        elif choice == '3':
            date_str = input("Enter the date of the inspection to remove (YYYY-MM-DD): ")
            date = datetime.datetime.strptime(date_str, '%Y-%m-%d')
            scheduler.remove_inspection(date)

        elif choice == '4':
            print("Exiting the program.")
            break

        else:
            print("Invalid choice, please try again.")

if __name__ == "__main__":
    main()
