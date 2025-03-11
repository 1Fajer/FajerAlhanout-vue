<template>
  <body>
    <div class="container-fluid d-flex flex-column p-0">
      <div class="row flex-grow-0 m-0 border-bottom">
        <div class="col m-0 py-1 ">
          <nav class="navbar navbar-expand-lg px-3 py-0">
            <div class="container-fluid d-flex justify-content-between align-items-center p-0">
              <div class="d-flex align-items-center">
                <div class="avatar-container position-relative my-1">
                  <img src="@/assets/id1.svg" class="rounded-circle avatar">
                  <span class="status-indicator"></span>
                </div>
                <small style="color:#98A4AE; font-weight: lighter; font-size: smaller;" class="ps-2">Away</small>
              </div>
              <div class="flex-grow-1"></div>
              <div class="navbar-icons d-flex align-items-center gap-4">
                <i class="bi bi-ban text-primary" @click="toggleBlockPopup"></i>
                <i class="bi bi-trash text-danger" @click="toggleDeletePopup"></i>
                <i class="bi bi-telephone text-secondary" @click="toggleUnblockPopup"></i>
                <i class="bi bi-camera-video text-secondary"></i>
                <i class="bi bi-list text-secondary"></i>
              </div>
            </div>
          </nav>
          
        </div>
      </div>

      <div class="row flex-grow-1 d-flex m-0">
        <div class="col-8 chat-section p-0 d-flex pt-2 flex-column m-0">
          <div class="chat-box ps-2 flex-grow-1">
            <div class="align-item-start"><img src="@/assets/id3.svg" class="avatar-sent me-2"><span style="font-size:xx-small; color:#98A4AE;"> Andrew, 2 hours ago</span></div>
            
            <div class="message received d-flex align-items-center ms-4">
              <span style="font-size:x-small;">If I don't like something, I'll stay away from it.</span>
            </div>
            <div class="text-end"><span style="font-size:xx-small; color:#98A4AE">2 hours ago</span></div>
            <div class="message sent d-flex align-items-center justify-content-end">
              <span style="font-size:x-small;">If I don’t like something, I’ll stay away from it.</span>
            </div>

            <div class="align-item-start"><img src="@/assets/id3.svg" class="avatar-sent me-2"><span style="font-size:xx-small; color:#98A4AE"> Andrew, 2 hours ago</span></div>
            <div class="message received d-flex align-items-center ms-4">
              <span style="font-size:x-small;">I want more detailed information.</span>
            </div>
            <div class="text-end"><span style="font-size:xx-small; color:#98A4AE">2 hours ago</span></div> 
            <div class="message sent d-flex align-items-center justify-content-end">
              <span style="font-size:x-small;">If I don't like something, I'll stay away from it.</span>
            </div>
            
            <div class="message sent d-flex align-items-center justify-content-end">
              <span style="font-size:x-small;">They got there early, and they got really good seats.</span>
            </div>

            <div class="align-item-start"><img src="@/assets/id3.svg" class="avatar-sent me-2"><span style="font-size:xx-small; color:#98A4AE"> Andrew, 2 hours ago</span></div>
            <div class="message received d-flex align-items-center ms-4">
              <img src="@/assets/img1.svg" class="thumb img-fluid rounded" >
            </div>
          </div>
          
			

          <div class="row">
                  <div class="col">
                    <div class="chat-input d-flex align-items-center gap-2 px-2 py-2 border-top">
                      <i class="bi bi-emoji-smile"></i>
                      <input type="text" class="form-control flex-grow-1 search p-0" style="font-size: x-small;" placeholder="Type a message">
                      <i class="bi bi-image"></i>
                      <i class="bi bi-paperclip"></i>
                      <i class="bi bi-mic"></i>
                    </div>
                  </div>
          </div>
        </div>
    
          
          
        <div class="col-4 media-section px-4 pt-3 d-flex flex-column flex-grow-1 border-start" >

          <p class="fw-semibold mt-2 mb-1 ps-1" style="font-size: small;">  Media <span style="color:#98A4AE ;font-size:x-small;">(36)</span></p>

          <div class="row g-2">
            <div class="col-4">
              <img src="@/assets/img1.svg" class="thumb img-fluid rounded">
            </div>
            <div class="col-4">
              <img src="@/assets/img2.svg" class="thumb img-fluid rounded">
            </div>
            <div class="col-4">
              <img src="@/assets/img3.svg" class="thumb img-fluid rounded">
            </div>
          </div>
          <div class="row g-2">
            <div class="col-4">
              <img src="@/assets/img4.svg" class="thumb img-fluid rounded">
            </div>
            <div class="col-4">
              <img src="@/assets/img1.svg" class="thumb img-fluid rounded">
            </div>
            <div class="col-4">
              <img src="@/assets/img2.svg" class="thumb img-fluid rounded">
            </div>

            <p class="fw-semibold my-3  ps-1 " style="font-size: small;">Files <span style="color:#98A4AE ;font-size:x-small;">(36)</span></p>
            <ul class="list-unstyled m-0 p-0 g-0">
              <li><img src="@/assets/1ado.svg" class="files"> service-task.pdf</li>
              <li><img src="@/assets/1fig.svg" class="files"> homepage-design.fig</li>
              <li><img src="@/assets/1chro.svg" class="files"> about-us.html</li>
              <li><img src="@/assets/1zip.svg" class="files"> work-project.zip</li>
              <li><img src="@/assets/1js.svg" class="files"> custom.js</li>
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

    <!-- Unblock User Popup -->
    <div class="popup-overlay" v-if="showUnblockPopup">
      <div class="popup-container">
        <div class="popup-icon">
          <i class="bi bi-unlock"></i>
        </div>
        <div class="popup-title">Unblock User</div>
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
  bottom: 0.2rem;
  right: 0.2rem;
  width: 0.6rem;
  height: 0.6rem;
  border-radius: 50%;
  background-color: green;
  border: 1px solid white;

}

.chat-box {
  overflow-y: auto;
  display: flex;
  flex-direction: column;
}


.message {
  padding: 2.5%;
  border-radius: 8px;
  margin-bottom:0.85rem;
}

.received {
  background: #EFF4FA;
  align-self: flex-start;
}

.sent {
  background: #ECFDFD;
  align-self: flex-end;
}

.avatar {
  width: 2.2rem;
  height: 2.2rem;
  border-radius: 50%;
}

.avatar-sent {
  width: 1.75rem;
  height: 1.75rem;
  border-radius: 50%;
  margin-bottom: 0.5rem;
}
.thumb {
  width: 3rem;
  height: 3rem;
  object-fit: cover;
  border-radius: 5px;

}

.chat-input i {
  cursor: pointer;
  font-size: 1rem;
}

.search{
  border: none;
}

.files{
  width: 2rem;
  height: 2rem;
}

.container-fluid, .row, .col {
  margin: 0;
  padding: 0;
}


li {
  margin-bottom: 1rem;
  font-size: small;
}

li:hover{
  color: #8964ce;
  cursor: pointer;
  font-weight: bold; 

}

hover:i{
cursor: pointer;

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
