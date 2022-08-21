<template>
    <div class="InfoBlock">
      <img src="@/assets/UserImg/Banner.png" alt="Banner">
      <div class="InfoBlock__User">
          <img src="@/assets/UserImg/Avatar.png" alt="Avatar">
          <h2>Ricardo Cooper</h2>
          <div>
          <!-- buttons whis svg icons -->
            <button>
              <svg width="16" height="12" viewBox="0 0 16 12" fill="none" xmlns="http://www.w3.org/2000/svg" class="IconUserInfo">
                <path d="M0.00300002 1.884L8 5.882L15.997 1.884C15.9674 1.37444 15.7441 0.895488 15.3728 0.545227C15.0016 0.194965 14.5104 -9.35847e-05 14 3.36834e-08H2C1.48958 -9.35847e-05 0.998447 0.194965 0.627178 0.545227C0.255908 0.895488 0.0326041 1.37444 0.00300002 1.884Z" fill="#9CA3AF"/>
                <path d="M16 4.118L8 8.118L0 4.118V10C0 10.5304 0.210714 11.0391 0.585786 11.4142C0.960859 11.7893 1.46957 12 2 12H14C14.5304 12 15.0391 11.7893 15.4142 11.4142C15.7893 11.0391 16 10.5304 16 10V4.118Z" fill="#9CA3AF"/>
              </svg>
              <span>Message</span>
            </button>
            <button>
              <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg" class="IconUserInfo">
                <path d="M0 1C0 0.447715 0.447715 0 1 0H3.15287C3.64171 0 4.0589 0.353413 4.13927 0.835601L4.87858 5.27147C4.95075 5.70451 4.73206 6.13397 4.3394 6.3303L2.79126 7.10437C3.90756 9.87832 6.12168 12.0924 8.89563 13.2087L9.6697 11.6606C9.86603 11.2679 10.2955 11.0492 10.7285 11.1214L15.1644 11.8607C15.6466 11.9411 16 12.3583 16 12.8471V15C16 15.5523 15.5523 16 15 16H13C5.8203 16 0 10.1797 0 3V1Z" fill="#9CA3AF"/>
              </svg>
              <span>Call</span>
            </button>
            <!-- /buttons whis svg icons -->
          </div>
      </div>
    </div>
</template>

<style scoped>
.InfoBlock{
    width: 100%;
    display: flex;
    flex-flow: column;
    justify-content: center;
    align-items: center;
}
.InfoBlock>img{
    border-radius:0 0 6px 6px;
}
.InfoBlock__User{
    display: flex;
    flex-flow: row;
    align-items: flex-end;
}

.InfoBlock__User>div{
    margin-left: 30rem;
}
.InfoBlock__User>img{
    margin-top: -4.5rem;
}
.InfoBlock__User>h2{
    margin-left: 1.5rem;
    padding-bottom: 0.5rem;
    font-size: 24px;
}
.InfoBlock__User>div>button{
    margin: 0 0.5rem;
    cursor: pointer;
    font-weight: 500;
    font-size: 14px;
    background-color: #fff;
    border-radius: 6px;
    border: 1px solid #D1D5DB;
    color: #000;
    padding: 10px 15px;
    transition: color,background-color  0.4s;
}
.InfoBlock__User>div>button:hover{
    background-color: rgb(95, 95, 95);
    color: rgb(255, 255, 255);
    transition:color,background-color 0.4s;
}

.InfoBlock__User>div>button:hover>svg>path{
    fill: #fff;
    transition: fill 0.2s;
}
.InfoBlock__User>div>button>svg{
    margin-bottom: -1px;
}

.InfoBlock__User>div>button>span{
    padding-left: 10px ;
}
</style>