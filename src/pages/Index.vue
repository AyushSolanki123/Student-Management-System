<template>
  <q-page padding>
    <div>
      <div class="row justify-between">
        <div class="text-subtitle1 q-pa-sm">
          Total Students: {{ students.length }}
        </div>
        <DialogButton
          class=""
          :label="'Add Student'"
          @atClick="showAddStudentDialog = true"
        />
      </div>
      <StudentDetails
        v-if="students.length"
        class="q-mt-md"
        :students="students"
        @deleteStudent="deleteStudent"
      />
      <div v-else class="flex flex-center">
        No students Added!!
      </div>
    </div>
    <AddStudentDialog
      :showDialog="showAddStudentDialog"
      @addStudent="addStudent"
      @closeDialog="showAddStudentDialog = false"
    />
  </q-page>
</template>

<script>
import DialogButton from 'src/components/DialogButton.vue';
import AddStudentDialog from 'src/components/AddStudentDialog.vue';
import StudentDetails from 'src/components/StudentDetails.vue';
export default {
  name: 'PageIndex',
  components: {
    DialogButton,
    StudentDetails,
    AddStudentDialog
  },
  data() {
    return  {
      showDialog: false,
      showAddStudentDialog: false,
      counter : 0,
      students: []
    }
  },
  methods: {
    counterClicked() {
      this.counter = this.counter + 1;
    },
    addStudent(value) {
      this.showAddStudentDialog = false
      const requestOptions = {
        method: "POST",
        headers: {
          "Content-type": "application/json"
        },
        body: JSON.stringify(value)
      }
      try {
        fetch("https://test-app-backend2.herokuapp.com/students", requestOptions)
          .then((response) => response.json())
          .then((data) => {
            this.students.push(data);
          })
      } catch (err) {
        this.students.push(value)
      }
    },
    deleteStudent(student) {
      const requestOptions = {
        method: "DELETE"        
      }
      try {
        fetch(`https://test-app-backend2.herokuapp.com/students/${student.id}`, requestOptions)
          .then((response) => {
            if (response.ok) {
              this.students.splice(this.students.indexOf(student), 1);
            }
          })
      } catch (err) {
        this.students.splice(this.students.indexOf(student), 1);
      }
    }
  },
  created() {
    try {
      fetch("https://test-app-backend2.herokuapp.com/students")
      .then((response) => response.json())
      .then((data) => {
        this.students = data;
      })
    } catch (err) {
      this.students = []
    }
  }
}
</script>

<style>
  .card {
    width: 25vw;
  }
  .my-card {
    width: 100%;
    max-width: 250px;
  }
</style>