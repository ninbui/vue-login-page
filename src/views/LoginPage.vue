<script>
    import { ref } from 'vue'

    export default {
       setup() {
        // 0: Home, 1: Login, 2:Register
        const mode = ref(0)

        const username = ref(null)
        const password = ref(null)
        const emailAddress = ref(null)
        const confirmPassword = ref(null)

        function onFormChange() {
            mode.value = mode.value==1 ? 2 : 1
            username.value = null
            password.value = null
            emailAddress.value = null
            confirmPassword.value = null
        }

        return {
            onFormChange,
            mode,
            username,
            password,
            emailAddress,
            confirmPassword,
        }
    }
    }
</script>

<template>
    <div class="container" :class="mode==1 ? 'login' : mode==2 ? 'register': 'home'">
        <div class="app-logo">
            <img src="../assets/app-img.jpg" alt="">
        </div>
        <div class="header" v-if="mode==0">
            <div class="app-name">
                Kitten
            </div>
            <div class="app-message">
                Health & Care Tips to keep your Cat healthy<br>
                A healthy cat is a happy cat!
            </div>
        </div>

        <div class="form" v-if="mode==1 || mode==2">
            <div class="header">
                <div class="form-title">
                    {{ mode==1 ? 'Login' : 'Register' }}
                </div>
                <div class="form-sub-title">
                    
                    {{ mode==1 ? 'Login to your account' : 'Create your account' }}
                </div>
            </div>
            <div class="colums">
                <div class="column-group" v-if="mode!=0">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><g fill="currentColor"><circle cx="12" cy="6" r="4"/><path d="M20 17.5c0 2.485 0 4.5-8 4.5s-8-2.015-8-4.5S7.582 13 12 13s8 2.015 8 4.5Z" opacity=".5"/></g></svg>
                    <input class="username" type="text" placeholder="Username" v-model="username">
                </div>
                <div class="column-group" v-if="mode==2">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><path fill="currentColor" d="m20 8l-8 5l-8-5v10h16zm0-2H4l8 4.99z" opacity=".3"/><path fill="currentColor" d="M4 20h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2H4c-1.1 0-2 .9-2 2v12c0 1.1.9 2 2 2zM20 6l-8 4.99L4 6h16zM4 8l8 5l8-5v10H4V8z"/></svg>
                    <input class="email-address" type="text" placeholder="Email address" v-model="password">
                </div>
                <div class="column-group" v-if="mode!=0">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><g fill="currentColor"><path d="M2 16c0-2.828 0-4.243.879-5.121C3.757 10 5.172 10 8 10h8c2.828 0 4.243 0 5.121.879C22 11.757 22 13.172 22 16c0 2.828 0 4.243-.879 5.121C20.243 22 18.828 22 16 22H8c-2.828 0-4.243 0-5.121-.879C2 20.243 2 18.828 2 16Z" opacity=".5"/><path d="M8 17a1 1 0 1 0 0-2a1 1 0 0 0 0 2Zm4 0a1 1 0 1 0 0-2a1 1 0 0 0 0 2Zm5-1a1 1 0 1 1-2 0a1 1 0 0 1 2 0ZM6.75 8a5.25 5.25 0 0 1 10.5 0v2.004c.567.005 1.064.018 1.5.05V8a6.75 6.75 0 0 0-13.5 0v2.055a23.57 23.57 0 0 1 1.5-.051V8Z"/></g></svg>
                    <input class="password" type="password" placeholder="Password" v-model="emailAddress">
                </div>
                <div class="column-group" v-if="mode==2">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><g fill="currentColor"><path d="M2 16c0-2.828 0-4.243.879-5.121C3.757 10 5.172 10 8 10h8c2.828 0 4.243 0 5.121.879C22 11.757 22 13.172 22 16c0 2.828 0 4.243-.879 5.121C20.243 22 18.828 22 16 22H8c-2.828 0-4.243 0-5.121-.879C2 20.243 2 18.828 2 16Z" opacity=".5"/><path d="M8 17a1 1 0 1 0 0-2a1 1 0 0 0 0 2Zm4 0a1 1 0 1 0 0-2a1 1 0 0 0 0 2Zm5-1a1 1 0 1 1-2 0a1 1 0 0 1 2 0ZM6.75 8a5.25 5.25 0 0 1 10.5 0v2.004c.567.005 1.064.018 1.5.05V8a6.75 6.75 0 0 0-13.5 0v2.055a23.57 23.57 0 0 1 1.5-.051V8Z"/></g></svg>
                    <input class="confirm-password" type="password" placeholder="Confirm password" v-model="confirmPassword">
                </div>
            </div>
            <div class="feature" v-if="mode==1">
                <div class="remember-me">
                    <input type="checkbox" name="checkbox" id="remember_me"/>
                    <label for="remember_me">Remember me</label>
                </div>
                <div class="forgot-pw">
                    <label>Forgot password?</label>
                </div>
            </div>
            <div class="message" v-if="mode==2">
                <span class='message'>By registing, you are agreeing to our<br>Terms of use and Privacy Policy.</span>
            </div>
            
        </div>

        <div class="footer">
            <div class="btn-group">
                <div id="login" class="btn login-btn" @click="mode=1" v-if="mode==0 || mode==1">
                    Login
                </div>
                <div id="register" class="btn register-btn" @click="mode=2" v-if="mode==0 || mode==2">
                    Register
                </div>
            </div>
            <div class="message" v-if="mode==1 || mode==2">
                <label>{{ mode==1 ? "Don't have an account?" : "Already have an account?" }}</label>
                <a @click="onFormChange()">{{ mode==1 ? "Register" : "Login" }}</a>
            </div>
        </div>

    </div>
</template>

<style lang="scss">




    .container {
        & * {
            text-align: center;
        }
        background-image: url("../assets/login-background.jpg");
        background-size: cover;
        width: 100vw;
        height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        overflow: hidden;
    }
    .app-logo {
        position: relative;
        text-align: center;
        img {
            width: 100%;
            width: 16rem;
            border-radius: 50%;
        }    
        
        .login &,
        .register & {
            position: absolute;
            transform: scale(1);
            animation: moveTop .5s 1 alternate;
            img {
                border-radius: 100% / 0 0 100% 100%;
                transition:  width .3s ease-in .3s, border-radius .5s ease-in .5s;
            }
        }

        .login & {
            top: -4rem;
            img {
                width: 100%;
                transition:  width .3s ease-in , border-radius .5s ease-in;
            }
        }

        .register &{
            top: -2rem;
            img {
                width: 16rem;
                transition:  width .3s ease-in , border-radius .5s ease-in;
            }
        }

        @keyframes moveTop {
            0% {
                top: 12rem;
                transform: scale(0);
            }
            50% {
                top: -10rem;
            }
            100% {
                transform: scale(1);
                top: -4rem;
            }
        }
    }

    .app-name {
        font-size: 6.25rem;
        font-weight: 700;
        line-height: 1;
    }

    // Form
    .form {
        z-index: 1;
        .header {
            .form-title {
                font-size: 3.75rem;
                font-weight: 700;
                text-align: center;
                line-height: 1.3;
            }
        }
        .colums {
            margin-top: 1rem;
            .column-group {
                position: relative;
                margin-top: .5rem;
                    
                input {
                    height: 3.125rem;
                    width: 20rem;
                    border-radius: 8px;
                    border: none;
                    padding: 1.25rem 3rem;
                    text-align: left;

                    &:focus,
                    &:focus-visible {
                        outline-color: #e59700;
                    }
                }
                svg {
                    position: absolute;
                    height: 100%;
                    width: 1.75rem;
                    left: .75rem;
                }
            }
        }
        .feature {
            display: flex;
            justify-content: space-between;
            margin-top:  0.5rem;
            .remember-me { 
                display: flex;
                align-items: center;
                gap: .5rem;

                input[type=checkbox] {
                    /* Add if not using autoprefixer */
                    -webkit-appearance: none;
                    /* Remove most all native input styles */
                    -moz-appearance: none;
                        appearance: none;
                    /* Not removed via appearance */
                    margin: 0;
                    font: inherit;
                    color: currentColor;
                    width: 1.25em;
                    height: 1.25em;
                    /* border: 0.15em solid currentColor; */
                    border: none;
                    background-color: #fff;
                    border-radius: 0.15em;
                    // transform: translateY(-0.075em);
                    display: grid;
                    place-content: center;
                    cursor: pointer;
                    &::before {
                        content: "";
                        width: 0.85em;
                        height: 0.85em;
                        -webkit-clip-path: polygon(14% 44%, 0 65%, 50% 100%, 100% 16%, 80% 0%, 43% 62%);
                                clip-path: polygon(14% 44%, 0 65%, 50% 100%, 100% 16%, 80% 0%, 43% 62%);
                        transform: scale(0);
                        /* transform-origin: bottom left; */
                        transition: transform .2s ease-in-out;
                        box-shadow: inset 1rem 1rem rebeccapurple;
                    }
                    &:checked::before {
                        transform: scale(1) rotate(5deg);
                    }
                }
            }
        }
        .message {
            display: flex;
            justify-content: center;
            span {
                text-align: left;
                font-size: .85rem;
            }

        }
    }
    
    // Footer
    .footer {
        display: flex;
        flex-direction: column;
        justify-content: center;
        .login &,
        .register &{
            position: absolute;
            bottom: 2rem;

            .register-btn {
                box-shadow: rgba(0, 0, 0, 0.45) 0px 25px 20px -20px !important;
                background: linear-gradient(90deg, hsl(46deg 100% 57.58%) 0%, hsl(176deg 82.02% 61.41%) 100%);
                color: #fff;
            }

        }

        .btn {
            height: 3.125rem;
            width: 20rem;
            display: flex;
            justify-content: center;
            align-items: center;
            border-radius: 10px;
            margin-top: 1.5rem;
            text-transform: uppercase;
            cursor: pointer;
            
            &.login-btn {
                box-shadow: rgba(0, 0, 0, 0.45) 0px 25px 20px -20px;
                background: linear-gradient(90deg, hsl(46deg 100% 57.58%) 0%, hsl(176deg 82.02% 61.41%) 100%);
                color: #fff;
            }

            &.register-btn {
                margin-top: 1.25rem;
                box-shadow: inset #34c5d5 0px 0px 0px 1px;
            }
        }
        
        .message {
            margin-top: .5rem;
            a {
                margin-left: 1rem;
                text-decoration: underline;
            }
        }

    }

    // iP ~8plus
    @media (min-height: 1024px),  (min-width: 500px){
        .login .app-logo {
            top: -2rem;
            img {
                width: 24rem;
                transition:  width .3s ease-in , border-radius .5s ease-in;
            }
        }

        .register .app-logo {
            top: -2rem;
            img {
                width: 20rem;
                transition:  width .3s ease-in , border-radius .5s ease-in;
            }
        }
    }


       


</style>



