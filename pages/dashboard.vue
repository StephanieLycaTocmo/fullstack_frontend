<template>
    <div>
        <NavBar />
        
        <div class="container">
            <h1>User Information</h1>
            <div>
                <table class="table table-bordered table-striped text-center">
                <thead class="thead-primary">
                    <tr>
                    <th scope="col">ID</th>
                    <th scope="col">User</th>
                    <th scope="col">Email</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>{{$auth.user.id}}</td>
                        <td>{{$auth.user.name}}</td>
                        <td>{{$auth.user.email}}</td>
                    </tr>
                </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<style>
h1 {
    text-align: center;
    padding-bottom: 25px;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}
.container {
    padding: 5px;
}
.text {
    text-align: center;
}
</style>