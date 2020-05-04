<template>
    <div id="employee-table" class="mt-2">
        <table class="table table-hover">
            <thead>
                <tr>
                    <th>First Name</th>
                    <th>Last Name</th>
                    <th>Email</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="employee in employees" :key="employee.id">
                    <td>{{ employee.firstName }}</td>
                    <td>{{ employee.lastName }}</td>
                    <td>{{ employee.email }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name: 'EmployeeTable',
    props: [
        'employees'
    ]
}
</script>