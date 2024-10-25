# Firebase-Tutorial
Firebase tutorial

#### step 1 : Clone the code 

#### step 2 : setup firebse and paste the configuration code (configration code example given below **Don't COPY THIS CONFIGRATION CODE IT'S UNIQUE FOR ALL**) on html file below body tag ( </body> )

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/9.12.1/firebase-app.js";

        // Your web app's Firebase configuration
        const firebaseConfig = {
            apiKey: "YOUR_API_KEY",
            authDomain: "YOUR_AUTH_DOMAIN",
            projectId: "YOUR_PROJECT_ID",
            storageBucket: "YOUR_STORAGE_BUCKET",
            messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
            appId: "YOUR_APP_ID"
        };

        // Initialize Firebase
        const app = initializeApp(firebaseConfig);
    </script>
    
    
    
#### step 3 :The below code in the script (consider the figure 1:import packages)

    import { getFirestore, addDoc, collection, getDocs } from 'https://www.gstatic.com/firebasejs/9.12.1/firebase-firestore.js'

![image](https://github.com/user-attachments/assets/d2115a20-f5c2-46ac-b763-f358b8c8b588)

    

#### step 4 : The below code for initialize database (note highlighted area Figure 3:Database initilizing)

     const db = getFirestore(app);
     
![image](https://github.com/user-attachments/assets/d404caf7-b8f7-4117-9a2c-8885ed7e4bf9)

     
#### step 5 : The below code to data sent (like in figure 2:data sending)

## Data send

     document.getElementById("submit-btn").onclick = async function (e) {
          e.preventDefault()
          const docRef = await addDoc(collection(db, "data"), {
              Name: document.getElementById('name').value,
              Message: document.getElementById('message').value
          });
          console.log("Document written with ID: ", docRef.id);
          location.reload()
      };
    
![image](https://github.com/user-attachments/assets/d2dfccda-f1f5-4963-90eb-fbbae6196f5d)


#### step 6 : The below code as in picture (note Figure 3:Data sending)

## Data Calling

         window.onload = async function () {
            const docs = await getDocs(collection(db, "data"));
            docs.forEach((doc) => {
                console.log(doc.data().Name)
                const myMessage = document.getElementById("my-messages");

                const messageElement = document.createElement("div");
                messageElement.className = "flex justify-end"; // Align to the right
                messageElement.innerHTML = `
                <div class="flex items-start gap-2.5">
                    <img class="w-8 h-8 rounded-full"
                        src="https://images.pexels.com/photos/45201/kitty-cat-kitten-pet-45201.jpeg" alt="Jese image">
                    <div
                        class="flex flex-col w-full max-w-[320px] leading-1.5 p-4 border-gray-200 bg-gray-100 rounded-se-xl rounded-s-xl dark:bg-gray-700">
                        <div class="flex items-center space-x-2 rtl:space-x-reverse">
                            <span class="text-sm font-semibold text-gray-900 dark:text-white">${doc.data().Name}</span>
                            <span class="text-sm font-normal text-gray-500 dark:text-gray-400">11:46</span>
                        </div>
                        <p class="text-sm font-normal py-2.5 text-gray-900 dark:text-white">${doc.data().Message}</p>
                        <span class="text-sm font-normal text-gray-500 dark:text-gray-400">Delivered</span>
                    </div>
                </div>
                `
                myMessage.appendChild(messageElement)
            });
        }

![image](https://github.com/user-attachments/assets/dae64b7f-6118-4888-b7eb-1dfdebaa49ca)


#### step 7 : Type somthing in website form and submit. Then refresh the website to see the change
