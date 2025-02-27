<template>
  <body>
    <div class="container-fluid vh-100 d-flex flex-column p-0 ">
      <div class="row flex-grow-0 m-0 border-bottom">
        <div class="col m-0 ">
          <nav class="navbar navbar-expand-lg px-3 py-0">
            <div class="container-fluid d-flex justify-content-between align-items-center p-0">
              <div class="d-flex align-items-center">
                <div class="avatar-container position-relative ms-0">
                  <img src="@/assets/avatar.svg" height="43px" width="43px" class="rounded-circle mt-2 ">
                  <span class="status-indicator"></span>
                </div>
                <a class="nav-link text-muted" href="#">Away</a>
              </div>
              <div class="flex-grow-1"></div>
              <div class="navbar-icons d-flex align-items-center">
                <i class="bi bi-ban me-2 text-primary" @click="toggleBlockPopup"></i>
                <i class="bi bi-trash me-2 text-danger" @click="toggleDeletePopup"></i>
                <i class="bi bi-telephone me-2 text-secondary" @click="toggleUnblockPopup"></i>
                <i class="bi bi-camera-video me-2 text-secondary"></i>
                <i class="bi bi-list text-secondary"></i>
              </div>
            </div>
          </nav>
          
        </div>
      </div>

      <div class="row flex-grow-1 d-flex mx-0">
        <div class="col-7 chat-section p-0 d-flex flex-column m-0 border-end">
          <div class="chat-box p-3 flex-grow-1">
            <div class="align-item-start"><img src="@/assets/avatar1.svg" class="avatar me-2"><span style="font-size:xx-small;"> Andrew, 2 hours ago</span></div>
            
            <div class="message received d-flex align-items-center">
              <span style="font-size:x-small;">If I don't like something, I'll stay away from it.</span>
            </div>
            <div class="text-end"><span style="font-size:xx-small;">2 hours ago</span></div>
            <div class="message sent d-flex align-items-center justify-content-end">
              <span style="font-size:x-small;">If I don’t like something, I’ll stay away from it.</span>
            </div>

            <div class="align-item-start"><img src="@/assets/avatar1.svg" class="avatar me-2"><span style="font-size:xx-small;"> Andrew, 2 hours ago</span></div>
            <div class="message received d-flex align-items-center">
              <span style="font-size:x-small;">I want more detailed information.</span>
            </div>
            <div class="text-end"><span style="font-size:xx-small;">2 hours ago</span></div> 
            <div class="message sent d-flex align-items-center justify-content-end">
              <span style="font-size:x-small;">If I don't like something, I'll stay away from it.</span>
            </div>
            
            <div class="message sent d-flex align-items-center justify-content-end">
              <span style="font-size:x-small;">They got there early, and they got really good seats.</span>
            </div>

            <div class="align-item-start"><img src="@/assets/avatar1.svg" class="avatar me-2"><span style="font-size:xx-small;"> Andrew, 2 hours ago</span></div>
            <div class="message received image d-flex align-items-center">
              <img src="@/assets/4image.png" class="thumb img-fluid rounded" style=" width: 60px; height: 60px;">
            </div>
          </div>
			

          <div class="row">
                  <div class="col">
                    <div class="chat-input d-flex px-2 align-items-center my-2 py-3 border-top">
                      <i class="bi bi-emoji-smile me-2"></i>
                      <input type="text" class="form-control flex-grow-1" placeholder="Type a message">
                      <i class="bi bi-file-earmark-image ms-2"></i>
                      <i class="bi bi-paperclip ms-2"></i>
                      <i class="bi bi-mic ms-2"></i>
                    </div>
                  </div>
          </div>
        </div>
          
          
        <div class="col-5 media-section p-3 g-0 d-flex flex-column">
          <h6 class="ms-3 mt-3 py-2">Media <span class="text-secondary">(36)</span></h6>

          <div class="row ms-2 mb-2 g-2">
            <div class="col-4">
              <img src="@/assets/3image.png" class="thumb img-fluid rounded">
            </div>
            <div class="col-4">
              <img src="@/assets/1image.png" class="thumb img-fluid rounded">
            </div>
            <div class="col-4">
              <img src="@/assets/2image.jpg" class="thumb img-fluid rounded">
            </div>
          </div>
          <div class="row ms-2 g-2">
            <div class="col-4">
              <img src="@/assets/3image.png" class="thumb img-fluid rounded">
            </div>
            <div class="col-4">
              <img src="@/assets/2image.jpg" class="thumb img-fluid rounded">
            </div>
            <div class="col-4">
              <img src="@/assets/4image.png" class="thumb img-fluid rounded">
            </div>

            <h6 class="ms-0 mt-4  me-0 py-3">Files <span class="text-secondary">(36)</span></h6>
            <ul class="list-unstyled">
              <li><i class="bi bi-filetype-pdf me-2"></i> service-task.pdf</li>
              <li><i class="bi bi-file-earmark"></i> homepage-design.fig</li>
              <li><i class="bi bi-filetype-html me-2"></i> about-us.html</li>
              <li><i class="bi bi-file-earmark-zip me-2"></i> work-project.zip</li>
              <li><i class="bi bi-filetype-js me-2"></i> custom.js</li>
            </ul>
          </div>


        </div> 
      </div>
    </div>

    

    <!-- Block User Popup -->
<div class="popup-overlay" v-if="showBlockPopup">
  <div class="popup-container">
    <div class="popup-icon">
      <i class="bi bi-slash-circle"></i>
    </div>
    <div class="popup-title">Block User</div>
    <div class="popup-message">You Are Going To Block This User, Are You Sure?</div>
    <div class="popup-buttons">
      <button class="cancel-btn" @click="cancelAction('block')">Cancel</button>
      <button class="confirm-btn" @click="confirmAction('block')">Yes</button>
    </div>
  </div>
</div>

<!-- Delete Conversation Popup -->
<div class="popup-overlay" v-if="showDeletePopup">
  <div class="popup-container">
    <div class="popup-icon">
      <i class="bi bi-trash"></i>
    </div>
    <div class="popup-title">Delete Conversation</div>
    <div class="popup-message">Once You Sure To Delete This Conversation, You Will Not Be Able To Undo This Action</div>
    <div class="popup-buttons">
      <button class="cancel-btn" @click="cancelAction('delete')">Cancel</button>
      <button class="confirm-btn" @click="confirmAction('delete')">Yes</button>
    </div>
  </div>
</div>

    <!-- Unlock User Popup -->
    <div class="popup-overlay" v-if="showUnblockPopup">
      <div class="popup-container">
        <div class="popup-icon">
          <i class="bi bi-unlock"></i>
        </div>
        <div class="popup-title">Unlock User</div>
        <div class="popup-message">You Are Going To Unblock This User, Are You Sure?</div>
        <div class="popup-buttons">
          <button class="cancel-btn" @click="cancelAction('unblock')">Cancel</button>
          <button class="confirm-btn" @click="confirmAction('unblock')">Yes</button>
        </div>
      </div>
    </div>
    
  </body>

</template>

<script>
export default {
  data() {
    return {
      avatar: "https://api.dicebear.com/9.x/lorelei/svg?backgroundColor=b6e3f4,c0aede,d1d4f9",
      showBlockPopup: false,
      showDeletePopup: false,
      showUnblockPopup: false
    };
  },
  methods: {
    // Toggle popup visibility methods
    toggleBlockPopup() {
      this.showBlockPopup = !this.showBlockPopup;
      this.showDeletePopup = false;
      this.showUnblockPopup = false;
    },
    toggleDeletePopup() {
      this.showDeletePopup = !this.showDeletePopup;
      this.showBlockPopup = false;
      this.showUnblockPopup = false;
    },
    toggleUnblockPopup() {
      this.showUnblockPopup = !this.showUnblockPopup;
      this.showBlockPopup = false;
      this.showDeletePopup = false;
    },
    // Confirmation methods
    confirmAction(type) {
      if (type === 'block') {
        this.showBlockPopup = false;
        // Additional block logic can be added here
      } else if (type === 'delete') {
        this.showDeletePopup = false;
        // Additional delete logic can be added here
      } else if (type === 'unblock') {
        this.showUnblockPopup = false;
        // Additional unblock logic can be added here
      }
    },
    cancelAction(type) {
      if (type === 'block') {
        this.showBlockPopup = false;
      } else if (type === 'delete') {
        this.showDeletePopup = false;
      } else if (type === 'unblock') {
        this.showUnblockPopup = false;
      }
    }
  }
};
</script>




<style scoped>

.avatar-container {
  position: relative;
  display: inline-block;
}

.status-indicator {
  position: absolute;
  bottom: 5px;
  right: 5px;
  width: 12px;
  height: 12px;
  background-color: #28a745;
  border: 2px solid white;
  border-radius: 50%;
}

.chat-box {
  background: transparent;
  height: 100%;
  width: 100%;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
  

}

.message {
  max-width: 75%;
  padding: 8px;
  border-radius: 10px;
  margin-bottom: 10px;
}

.received {
  background: #e9ecef;
  align-self: flex-start;
}

.sent {
  background: #d1ecf1;
  align-self: flex-end;
}

.avatar {
  width: 35px;
  height: 35px;
  border-radius: 50%;
}

.thumb {
  width: 100%;
  object-fit: cover;
  border-radius: 5px;
}

.chat-input i {
  cursor: pointer;
  font-size: 1.2rem;
  color: #6c757d;
  
}

.container-fluid, .row, .col {
  margin: 0;
  padding: 0;
}

@media (max-width: 768px) {
  .navbar-icons i {
    font-size: 1.5rem;
  }

  .chat-input i {
    font-size: 1rem;
    position: absolute; /* Stick to the bottom */
    bottom: 0;
    left: 50%;
    transform: translateX(-50%); /* Center it horizontally */
    width: 95%; 
  
    
}


  .thumb {
    max-width: 100%;
    height: auto;
  }
}



li {
  margin-bottom: 1.5rem;
  font-size: small;
}

li:hover{
  color: #8964ce;
  text-decoration: underline;
}

/* Popup Styles */
.popup-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.popup-container {
  background-color: white;
  border-radius: 10px;
  padding: 20px;
  width: 300px;
  text-align: center;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.popup-icon {
  font-size: 2rem;
  margin-bottom: 10px;
}

.popup-title {
  font-weight: bold;
  margin-bottom: 10px;
}

.popup-message {
  margin-bottom: 20px;
  font-size: 0.9rem;
  color: #6c757d;
}

.popup-buttons {
  display: flex;
  justify-content: space-between;
}

.cancel-btn {
  background-color: #6c757d;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 5px;
  cursor: pointer;
  width: 45%;
}

.confirm-btn {
  background-color: #4e54f7;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 5px;
  cursor: pointer;
  width: 45%;
}

</style>
