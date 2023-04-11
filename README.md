# -Learn-to-use-OpenAI-API-by-building-ChatGPT-super-simple-React-Node.js

https://raw.githubusercontent.com/RodrigoMvs123/-Learn-to-use-OpenAI-API-by-building-ChatGPT-super-simple-React-Node.js/main/README.md

https://www.youtube.com/watch?v=JJ9fkYX7q4A

Terminal 
aniakubow@Anias-MacBook-Pro ~% cd WebstormProjects 
aniakubow@Anias-MacBook-Pro WebstormProjects % npx create-react-app react-chatgpt-clone 


App.js 
import { useState, useEffect } from ‘react’

const App = () => {
       const [ value, setValue ] = useState(null)
       const [ message, setMessage ] = useState(null) 
       const [ previousChats, setPreviousChats ] = useState([])       
       const [ currentTitle, setCurrentTitle ] = ([null]) 

       const createNewChat = () => {
                setMessage(null)
                setValue = (“”)
                setCurrentTitle(null)
}

       const handleClick = (uniqueTitle) => {
                setCurrentTitle(uniqueTitle)
                setMessage(null)
                setValue = (“”)
}

       const getMessages = async () => {
               const options = {
                   method: “POST”,
                   body: JSON.stringify ( {
                       message: value
)},
                   headers: {
                       “Content-Type”: “application/json”
}

}
               try {
                     const response = await fetch (‘localhost8000/completions’, options)  
                     const data = await response.json ()
                     setMessage(data.choices[0].message) 
} catch (error) {
               console.error (error)
     }
}

useEffect(() => {
          console.log(currentTitle, value, message)
          if (!currentTitle && value && message) {
                    setCurrentTitle(value)
}

         if (currentTitle && value && message) {
          setPreviousChat(prevChats => (
                     [...prevChats, 
                        {
                         title: currentTitle, 
                         role: “user”
                         content: value
                        }, 
                       { 
                         title: currentTitle,
                         role: message.role,
                         content: message.content
                          }
        ]
))
}
} [message, currentTitle])

console.log (previousChats)

const currentChat = previousChats.filter(previousChats => previousChat.title === currentTitle)
const uniqueTitles = Array.from newSet ( previousChats.map(previousChats => previousChat.title)
console.log(uniqueTitles)

       return  (
           <div className=”app”>
               <section className=”side-bar”>
                    <button onClick={createNewChat}>+ New chat</button>
                    <ul className=”history”></ul>
                          {uniqueTitles?.map ((uniqueTitle, index) => <li key={index}onClick {()=> handleClick (uniqueTitle)>uniqueTitle</li>)}
                    <nav>
                       <p>Made by Ania</p>
                    </nav>
               </section>
               <section className=”main”>
                         {!currentTitle && <h1>AniaGPT</h1>}
                         <ul className=”feed”>
                              {currentChat?.map((chatMessage, index ) => <li key={index}>
                                     <p className=”role”>{chatMessage.role}</p>
                                     <p>{chatMessage.content}</p>
                          </li>)}
                     </ul>
                     <div className=”bottom-section”>
                          <div className=”input-container”>
                              <input value ={value} onChange={(e)  => setValue(e.target.value)}/>
                          <div id=”submit” onClick={getMessages}>https://www.compart.com/en/unicode/U+27A2</div>
                          </div>
                          <p className=”info”>
                              Chat GPT Mar 14 Version. Free Research Preview.
                              Our goal is to make AI systems more natural and safe to interact with.
                              Your feedback will help us improve.  
                          </p>
                     </div>
             </section>
           </div>
 )
}

export default App

localhost8000/completions

index.css
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;500;600;700;800&display=swap');

* {
       color: #fff;
       font-family: 'Open Sans', sans-serif;

}

body {
       margin: 0;
       padding: 0;
}

.app {
       background-color: #343541;
       display: flex;
}

.side-bar {
        background-color: #202123;
        height: 100v;
        width: 244px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
 
}

button {
       border: solid 0.5 px rgba (255, 255, 255, 0.5);
       background-color: transparent;
       border-redius: 5px;
       padding: 10px;
       margin: 10px;
}

nav {
       border top: solid 0.5 px rgba (255, 255, 255, 0.5) ;
       padding: 10px;
       margin: 10px;

}

.history {
       padding: 10px;
       margin: 10px;
       height: 100%; 
}

.history li {
       list-style-type: none;
       padding: 15px 0;
       cursor: pointer; 
}

.main {
         height: 100vh;
         width: 100%;
         display: flex;
         flex-direction: column;
         justify-content: space-between;
         align-items: center;  
         text-align: center;
}

.info {
        color: rgba: (255, 255, 255, 0.5);
        font-size: 11px;
        padding: 10px;
            
}

.bottom:section {
        width: 100%;
        display: flex; 
        flex-direction: column;
        justify-content: center;
        align-items: center;
        
}

.input-container {
        position: relative;
        input: 100%;
        max-width: 650px;
        
}

.input {
        width: 100%;
        border: none;
        font-size: 20px;
        back-groundcolor: rgba ( 255, 255, 255, 0.05 );
        padding: 12px 15px;
         border-radius: 5px;
         box-shadow: rgba ( 0, 0, 0, 0.05 ) 0 54px 55px,
                     rgba ( 0, 0, 0, 0.05 ) 0 -12 px 30px,
                     rgba ( 0, 0, 0, 0.05 ) 0 4px 6px ,
                     rgba ( 0, 0, 0, 0.05 ) 0 12px 3px,
                     rgba ( 0, 0, 0, 0.05 ) 0 -3px 5px;

}

.input:focus {
          outline: none;
          
}

#submit {
          position: absolut;
          bottom: 15px; 
          right: 0;
          cursor: pointer;
} 

.feed {
         overFlow: escroll;
         width: 100%;
         padding: 0%;
}

.feed li {
         display: flex;
         background-color: #444654;
         width: 100%;
         padding: 20px;
         margin: 20px 0;
}

.feed p {
         color: rgba(255, 255, 255, 0.8);
         font-size: 14px;
         text-align: left;
}

.feed p.role {
         min-width: 100%;
}

https://fonts.google.com/

index.js 
import react from ‘react’
import reactDOM from ‘react-dom/client’
import ‘./App’
import App from ‘./App’

const root = ReactDom.createRoot(document.getElementById(‘root’))
root render (
       <React.StrictMode>
              <’App />
       <React.StrictMode>’
)

aniakubow@Anias-MacBook-Pro ~% cd WebstormProjects 
aniakubow@Anias-MacBook-Pro WebstormProjects % cd react-chatgpt-clone
aniakubow@Anias-MacBook-Pro react-chatgpt-clone % npm run start

localhost:3000 (website)






server.js
const PORT = 8000
const express = require (‘express’)
const cors = require (‘cors’)
require (‘dotenv’).config()
const app = express ()
app.use (express.json())
app.use (cors ())

const API_KEY = process.env.API_KEY

app.post(‘/completions’, async (req, resp) => {
      const options = {
           method: “POST”,
           headers: {
                “Authorization”: ‘Bearer ${API_KEY}’,
                 “Content-Type”: “application/json” 
},

body: JSON stringify ({
          model: “gpt-3.5-turbo”,
          messages [{role: “user”, content:req.body.message}].
          max-tokens: 100, 
})

}
      try {
          const response = await fetch(‘https://api.openai.com/v1/chat/completions’, options)
          const data = await respons.json()
          res.send(data)
}catch (error) {
           console.error(error)
}
} ) // localhost:8000/completions

app.listen (PORT, ()  => console.log ( ‘Your server is running on PORT’ + PORT ))



aniakubow@Anias-MacBook-Pro react-chatgpt-clone % npm i cors express nodemon
aniakubow@Anias-MacBook-Pro react-chatgpt-clone %

package.json
“scripts”: {
      “start:frontend”: “react-scripts start”
      “start:backend”: “nodemon server.js”
} 
aniakubow@Anias-MacBook-Pro react-chatgpt-clone % npm run start:frontend
aniakubow@Anias-MacBook-Pro react-chatgpt-clone % npm run start:backend

aniakubow@Anias-MacBook-Pro react-chatgpt-clone %npm i dotenv

aniakubow@Anias-MacBook-Pro react-chatgpt-clone % npm run start:backend

https://platform.openai.com/docs/api-reference
https://platform.openai.com/account/api-keys 
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
https://platform.openai.com/docs/api-reference/chat/create 
POST https://api.openai.com/v1/chat/completions 

.env 
API_KEY= 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

