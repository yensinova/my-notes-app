<script setup></script>

<template>
    <header class="header">
        <h1 class="title">Notes Page</h1>
        <nav>
            <ul class="nav-list">
                <li>
                    <router-link to="/" class="link">Home</router-link>
                </li>
                <li>
                    <router-link to="/notes" class="link">Notes</router-link>
                </li>
            </ul>
        </nav>
    </header>
</template>

<style>
    .header {
        background-color: #000022;
        color: white;
        padding: 30px;
        text-align: center;

        .title {
            margin: 0;     
        }

        .nav-list {
            display: flex; 
            justify-content: space-around;
            .link {
                color: white;
                text-decoration: none;
            }
        }
    }
</style>