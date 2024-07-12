<template>
    <div class="navbar">
        <div class="nav-left">
            <div class="icons">
                <img
                    src="../../public/assets/Icons.svg"
                    alt="icons"
                />
            </div>
            <input
                type="text"
                class="search"
                placeholder="Search here..."
            />
            <img
                src="../../public/assets/searchNormal.svg"
                alt="icons"
                class="searchIcon"
            />
        </div>
        <div class="nav-right">
            <div class="account">
                <img
                    src="../../public/assets/users.svg"
                    alt="profile"
                />
                <div class="name-email">
                    <div class="name">{{ `${user.name}` }}</div>
                    <div class="email">{{ `${user.email}` }}</div>
                </div>
            </div>
            <div class="dropdown">
                <img
                    src="../../public/assets/arrowDown.svg"
                    alt="dropdown"
                />
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ["user"],
};
</script>
