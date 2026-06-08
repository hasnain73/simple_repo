# simple_repo
let student = {
  name: "Kishore",
  grade: 75,
  subjects: ["Math", "Science", "English"],

  displayInfo: function () {
    console.log("Name:", this.name);
    console.log("Grade:", this.grade);
    console.log("Subjects:", this.subjects.join(", "));
  }
};

// Call function
student.displayInfo();

// Add dynamic property
student.isPassed = student.grade >= 50;

// Loop through object
for (let key in student) {
  console.log(key + ":", student[key]);
}