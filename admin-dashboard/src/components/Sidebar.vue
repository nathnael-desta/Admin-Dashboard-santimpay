<template>
    <div class="sidebar">
        <div class="title"><span class="colored">Santim</span>Events</div>
        <div class="tabs">
            <div 
            class="dashboard-tab"
            :class = "{chosen: tabNo == 0}"
            @click="changeTab(0)"
            >
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M10.5 19.9V4.1C10.5 2.6 9.86 2 8.27 2H4.23C2.64 2 2 2.6 2 4.1V19.9C2 21.4 2.64 22 4.23 22H8.27C9.86 22 10.5 21.4 10.5 19.9Z" stroke="white" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M22 10.9V4.1C22 2.6 21.36 2 19.77 2H15.73C14.14 2 13.5 2.6 13.5 4.1V10.9C13.5 12.4 14.14 13 15.73 13H19.77C21.36 13 22 12.4 22 10.9Z" stroke="white" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M22 19.9V18.1C22 16.6 21.36 16 19.77 16H15.73C14.14 16 13.5 16.6 13.5 18.1V19.9C13.5 21.4 14.14 22 15.73 22H19.77C21.36 22 22 21.4 22 19.9Z" stroke="white" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
</svg>

                <div class="text">Dashboard</div>
            </div>
            <div 
              class="events-tab"
              :class = "{chosen: tabNo == 1}"
              @click="changeTab(1)"
              >
              <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M8 2V5" stroke="#292D32" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M16 2V5" stroke="#292D32" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M3.5 9.08984H20.5" stroke="#292D32" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M21 8.5V17C21 20 19.5 22 16 22H8C4.5 22 3 20 3 17V8.5C3 5.5 4.5 3.5 8 3.5H16C19.5 3.5 21 5.5 21 8.5Z" stroke="#292D32" stroke-width="1.5" stroke-miterlimit="10" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M15.6947 13.7002H15.7037" stroke="#292D32" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M15.6947 16.7002H15.7037" stroke="#292D32" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M11.9955 13.7002H12.0045" stroke="#292D32" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M11.9955 16.7002H12.0045" stroke="#292D32" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M8.29431 13.7002H8.30329" stroke="#292D32" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M8.29431 16.7002H8.30329" stroke="#292D32" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
</svg>

                <div class="text">Events</div>
            </div>
            <div 
              class="tickets-tab"
              :class = "{chosen: tabNo == 2}"
              @click="changeTab(2)"
              >
              <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M19.5 12.5C19.5 11.12 20.62 10 22 10V9C22 5 21 4 17 4H7C3 4 2 5 2 9V9.5C3.38 9.5 4.5 10.62 4.5 12C4.5 13.38 3.38 14.5 2 14.5V15C2 19 3 20 7 20H17C21 20 22 19 22 15C20.62 15 19.5 13.88 19.5 12.5Z" stroke="#292D32" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M10 4L10 20" stroke="#292D32" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round" stroke-dasharray="5 5"/>
</svg>

                <div class="text">Tickets</div>
            </div>
            <div 
              class="locations-tab"
              :class = "{chosen: tabNo == 3}"
              @click="changeTab(3)"
              >
              <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M12 13.4299C13.7231 13.4299 15.12 12.0331 15.12 10.3099C15.12 8.58681 13.7231 7.18994 12 7.18994C10.2769 7.18994 8.88 8.58681 8.88 10.3099C8.88 12.0331 10.2769 13.4299 12 13.4299Z" stroke="#292D32" stroke-width="1.5"/>
<path d="M3.61995 8.49C5.58995 -0.169998 18.42 -0.159997 20.38 8.5C21.53 13.58 18.37 17.88 15.6 20.54C13.59 22.48 10.41 22.48 8.38995 20.54C5.62995 17.88 2.46995 13.57 3.61995 8.49Z" stroke="#292D32" stroke-width="1.5"/>
</svg>

                <div class="text">Locations</div>
            </div>
            <div 
              class="users-tab"
              :class = "{chosen: tabNo == 4}"
              @click="changeTab(4)"
              >
              <svg width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M30.2333 36.0332C28.7666 36.4666 27.0333 36.6666 24.9999 36.6666H14.9999C12.9666 36.6666 11.2333 36.4666 9.7666 36.0332C10.1333 31.6999 14.5833 28.2832 19.9999 28.2832C25.4166 28.2832 29.8666 31.6999 30.2333 36.0332Z" stroke="#292D32" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M24.9999 3.3335H14.9999C6.66659 3.3335 3.33325 6.66683 3.33325 15.0002V25.0002C3.33325 31.3002 5.23325 34.7502 9.76659 36.0335C10.1333 31.7002 14.5833 28.2834 19.9999 28.2834C25.4166 28.2834 29.8666 31.7002 30.2333 36.0335C34.7666 34.7502 36.6666 31.3002 36.6666 25.0002V15.0002C36.6666 6.66683 33.3333 3.3335 24.9999 3.3335ZM19.9999 23.6168C16.6999 23.6168 14.0332 20.9335 14.0332 17.6335C14.0332 14.3335 16.6999 11.6668 19.9999 11.6668C23.2999 11.6668 25.9666 14.3335 25.9666 17.6335C25.9666 20.9335 23.2999 23.6168 19.9999 23.6168Z" stroke="#292D32" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M25.9668 17.6332C25.9668 20.9332 23.3001 23.6165 20.0001 23.6165C16.7001 23.6165 14.0334 20.9332 14.0334 17.6332C14.0334 14.3332 16.7001 11.6665 20.0001 11.6665C23.3001 11.6665 25.9668 14.3332 25.9668 17.6332Z" stroke="#292D32" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
</svg>

                <div class="text">Users</div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  props: ['tabNo', 'changeTab']
};
</script>
