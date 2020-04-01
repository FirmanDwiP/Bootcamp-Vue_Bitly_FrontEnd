<template>
  <div class="hello">

    <div class="container" style="margin-top: 50px;">
      <div class="row">
          <div class="col-md-2"></div>
          <div class="col-md-8">
            <h1 class="text-center">URL Singkat</h1>
            <form action="/shortUrls" method="POST" class="my-4 form-inline">
              <label for="fullUrl" class="sr-only">Url</label>
              <input required placeholder="Masukkan Url" type="url" name="fullUrl" id="fullUrl" class="form-control col mr-2">
              <button class="btn btn-primary" type="submit">Pendekkan</button>
            </form>
            
            <table class="table table-striped table-responsive text-center" style="margin:auto; text-align: center;">
              <thead>
                <tr>
                  <th>URL Asli</th>
                  <th>URL Pendek</th>
                  <th>Jumlah Click</th>
                </tr>
              </thead>
              <tbody>
                <% shortUrls.forEach(shortUrl => { %>
                  <tr>
                    <td><a href="<%= shortUrl.full %>"><%= shortUrl.full %></a></td>
                    <td><a href="<%= shortUrl.short %>"><%= shortUrl.short %></a></td>
                    <td><%= shortUrl.clicks %></td>
                  </tr>
                <% }) %>
              </tbody>
            </table>
          </div>
          <div class="col-md-2"></div>
      </div>
  </div>
</template>

<script>
import axios from 'axios';
const baseURL = 'http://localhost:4000/';
// const axios = require('axios');
export default {
  data () {
    return {
      todos: [],
      id: '',
      taskname: '',
      isEdit: false
    }
  },
  mounted () {
    this.getTasks()
  },
  methods: {
    getTasks () {
      axios({ method: 'GET', baseURL }).then(
        result => {
          console.log(result.data)
          this.todos = result.data
        },
        error => {
          console.error(error)
        }
      )
    }
  }
}
    </script>