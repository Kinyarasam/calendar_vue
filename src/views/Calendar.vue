<template>
    <div class="bg-gray-200 min-h-screen text-xs flex justify-center items-center font-mono">
        <div class="bg-white p-2 h-[450px] md:w-[500px] lg:w-[800px] w-72  rounded-xl shadow-md">
            <div class="flex flex-col justify-center">
                <!-- header -->
                <header>
                    <div class="flex justify-center items-center md:text-5xl text-3xl text-teal-800 uppercase font-sans font-bold py-2 ">
                        {{ WeekDaysFullNames[currentDay] }}
                    </div>
                    <div class="flex justify-center items-center rounded-xl text-slate-700">
                        <div class="flex flex-col px-1 items-center">
                            <span @click="dateDown" class="material-icons hover:bg-rose-500 text-rose-500 bg-gray-100 hover:text-white hover:shadow cursor-pointer w-6 h-6 flex items-center justify-center rounded-full">arrow_drop_up</span>
                            <span class="text-xl font-semibold py-1.5">
                                {{ currentDate.date }}
                            </span>
                            <span @click="dateUp" class="material-icons hover:bg-rose-500 text-rose-500 bg-gray-100 hover:text-white hover:shadow cursor-pointer w-6 h-6 flex items-center justify-center rounded-full">arrow_drop_down</span>
                        </div>
                        <div class="flex flex-col px-1 items-center">
                            <span @click="monthDown" class="material-icons hover:bg-rose-500 text-rose-500 bg-gray-100 hover:text-white hover:shadow cursor-pointer w-6 h-6 flex items-center justify-center rounded-full">arrow_drop_up</span>
                            <span class="text-xl font-semibold py-1.5">
                                {{ month[currentDate.month] }}
                            </span>
                            <span @click="monthUp" class="material-icons hover:bg-rose-500 text-rose-500 bg-gray-100 hover:text-white hover:shadow cursor-pointer w-6 h-6 flex items-center justify-center rounded-full">arrow_drop_down</span>
                        </div>
                        <div class="flex flex-col px-1 items-center">
                            <span @click="currentDate.year -= 1" class="material-icons hover:bg-rose-500 text-rose-500 bg-gray-100 hover:text-white hover:shadow cursor-pointer w-6 h-6 flex items-center justify-center rounded-full">arrow_drop_up</span>
                            <span class="text-xl font-semibold py-1.5">
                                {{ currentDate.year }}
                            </span>
                            <span @click="currentDate.year += 1" class="material-icons hover:bg-rose-500 text-rose-500 bg-gray-100 hover:text-white hover:shadow cursor-pointer w-6 h-6 flex items-center justify-center rounded-full">arrow_drop_down</span>
                        </div>
                        
                    </div>
                </header>
                <!-- /header -->

                <!-- section -->
                <section class="mt-16 px-2 lg:px-24">
                    <div class=" font-semibold rounded-xl overflow-hidden p-1.5 shadow-inner">
                        <div class="grid grid-cols-7 justify-center items-center">
                            <div v-for="day in WeekDays" :key="day" class="shadow-inner first:bg-red-500">
                                <div class="lg:w-[84px] md:w-[66px] w-[35px] border place-self-center p-2">
                                    {{ day }}
                                </div>
                            </div>
                        </div>
                        <div class="first:bg-red-500 grid grid-cols-7 items-center h-[180px] bg-gray-100 rounded-b-xl">
                            <div 
                                class="first:bg-red-500 border-2 text-slate-300 hover:bg-teal-800 hover:text-white p-2" 
                                v-for="(n, index) in (firstMonthDay)" 
                                :key="'prev' + index"
                            >
                                {{ (prevMonthDays) - firstMonthDay + n}}
                            </div>
                            <div v-for="(i, index) in currentMonthDays"  :key="'day' + index"
                                :class="{ active: i === currentDate.date}"  
                                class="first:bg-red-500 border-2 p-2 font-semibold text-slate-900 hover:bg-teal-800 hover:text-white" 
                            >
                            <!-- TODO: Add css To the last Day of the week -->
                                    {{i}}
                            </div>
                            <div class="first:bg-red-500 border-2 text-slate-300 hover:bg-teal-800 hover:text-white p-2" v-for="(n, index) in (35 - (currentMonthDays + firstMonthDay))" :key="'next' + index">
                                {{n}}
                            </div>
                        </div>
                    </div>
                </section>
            </div>
            
            <!-- <div class="flex border-b py-2 items-center">
                <button class="border rounded-full h-8 w-8 flex items-center justify-center"> <span class="material-icons">chevron_left</span></button>
                <div>
                    div
                    <span>June </span> 
                    <span>1</span>,
                    <span>2022</span>
                </div>
                <button  class="border rounded-full h-8 w-8 flex items-center justify-center"> <span class="material-icons">chevron_right</span></button>
            </div>
            <div class="shadow-inner my-4">
                
            </div> -->
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            WeekDays: ['Sun', 'Mon', 'Tue', 'Wed', 'Thur', 'Fri', 'Sat'],
            WeekDaysFullNames: ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"],
            month: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'],
            currentDate: {
                date: 0,
                month: 0,
                year: 0
            },
            DayOfTheWeek: [],
            active: true,
        }
    },
    computed: {
        prevMonthDays() {
            let year = this.currentDate.month === 0 ? this.currentDate.year - 1 : this.currentDate.year
            let month = this .currentDate.month === 0 ? 11 : this.currentDate.month

            return new Date(year, month, 0).getDate()
        },
        firstMonthDay() {
            let firstDay = new Date(this.currentDate.year, this.currentDate.month, 1).getDay()

            if (firstDay === 0) 
                firstDay = 7

            return (firstDay)
        },
        currentDay() {
            return new Date(
                this.currentDate.year, this.currentDate.month, this.currentDate.date
            ).getDay()
        },
        currentMonthDays() {
            return new Date(
                this.currentDate.year, this.currentDate.month + 1, 0
            ).getDate()
        }
    },
    methods: {
        dateUp() {
            // console.log(this.currentMonthDays)            

            if (this.currentDate.date == this.currentMonthDays) {
                this.currentDate.date = 1
                this.monthUp()
            }
            else{
                this.currentDate.date += 1
            }

            console.log(this.currentDate.date)
        },
        dateDown() {
            // console.log(this.currentMonthDays)            
            if (this.currentDate.date === 1) {
                this.currentDate.date = this.prevMonthDays
                this.monthDown()

                console.log(this.currentDate.date)
            }
            else{
                this.currentDate.date -= 1
            }
        },
        monthUp() {
            this.currentDate.month += 1
        },
        monthDown() {
            this.currentDate.month -= 1
        },
        getCurrentDate() {
            let today = new Date()

            this.currentDate.date = today.getDate()
            this.currentDate.month = today.getMonth()
            this.currentDate.year = today.getFullYear()
        },
    },
    created() {
        this.getCurrentDate()     
    },
}
</script>

<style scoped>
.active {
    background-color: #e33040;
    color: #fff,
}
</style>