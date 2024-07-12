<template>
  <div class="content">
                <div class="title">Dashboard</div>
                <div class="total-events block">
                    <div class="left">
                        <div class="title">Total Events</div>
                        <div class="number">{{ `${user.totalEvents}` }}</div>
                    </div>
                    <div class="right">
                        <img
                            src="../../public/assets/eventChart.svg"
                            alt=""
                        />
                        <div class="percentage">
                            <div class="green">
                                <img
                                    src="../../public/assets/smallGreenCircle.svg"
                                    alt=""
                                />
                                <div class="text">
                                    {{ `${user.eventsActive}` }}% Active
                                </div>
                            </div>
                            <div class="red">
                                <img
                                    src="../../public/assets/smallRedCircle.svg"
                                    alt=""
                                />
                                <div class="text">
                                    {{ `${user.eventsInactive}` }}% Inactive
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="sub-events">
                    <div class="left block">
                        <div class="left">
                            <div class="top">
                                <div class="title">Total Tickets</div>
                                <div class="number">
                                    {{ `${user.totalTickets1}` }}
                                </div>
                            </div>
                            <div class="bottom">
                                <div class="green">
                                    <img
                                        src="../../public/assets/smallGreenCircle.svg"
                                        alt=""
                                    />
                                    <div class="text">
                                        {{ `${user.tickets1Active}` }}% Active
                                    </div>
                                </div>
                                <div class="red">
                                    <img
                                        src="../../public/assets/smallRedCircle.svg"
                                        alt=""
                                    />
                                    <div class="text">
                                        {{ `${user.tickets1Inactive}` }}%
                                        Inactive
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="right">
                            <div class="status">
                                <div class="text">Status</div>
                                <img
                                    src="../../public/assets/yellowArrowDown.svg"
                                    alt=""
                                />
                            </div>

                            <img
                                src="../../public/assets/ticketChart.svg"
                                alt=""
                            />
                        </div>
                    </div>
                    <div class="right block">
                        <div class="left">
                            <div class="top">
                                <div class="title">Total Tickets</div>
                                <div class="number">
                                    {{ `${user.totalTickets2}` }}
                                </div>
                            </div>
                            <div class="bottom">
                                <div class="green">
                                    <img
                                        src="../../public/assets/smallGreenCircle.svg"
                                        alt=""
                                    />
                                    <div class="text">
                                        {{ `${user.tickets2Active}` }}% Active
                                    </div>
                                </div>
                                <div class="red">
                                    <img
                                        src="../../public/assets/smallRedCircle.svg"
                                        alt=""
                                    />
                                    <div class="text">
                                        {{ `${user.tickets2Inactive}` }}%
                                        Inactive
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="right">
                            <div class="status">
                                <div class="text">Status</div>
                                <img
                                    src="../../public/assets/yellowArrowDown.svg"
                                    alt=""
                                />
                            </div>

                            <img
                                src="../../public/assets/eventChart.svg"
                                alt=""
                            />
                        </div>
                    </div>
                </div>
            </div>
</template>

<script>
export default {
  props: ["user"]
}
</script>