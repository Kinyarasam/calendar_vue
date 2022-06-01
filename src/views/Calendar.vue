<template>
    <div class="bg-gray-200 min-h-screen text-xs flex justify-center items-center font-mono">
        <div class="bg-white p-2 h-[450px] md:w-[500px] lg:w-[800px] w-72  rounded-xl shadow-md">
            <div class="flex justify-center">
                <div>
                    <div class="flex justify-center items-center md:text-5xl text-3xl text-teal-800 uppercase font-sans font-bold py-2 ">
                        {{ WeekDaysFullNames[currentDay] }}
                    </div>
                    <div class="flex justify-center items-center shadow-inner rounded-xl text-slate-700">
                        <div class="flex flex-col px-1 items-center">
                            <span class="material-icons hover:bg-rose-500 text-rose-500 bg-gray-100 hover:text-white hover:shadow cursor-pointer w-6 h-6 flex items-center justify-center rounded-full">arrow_drop_up</span>
                            <span class="text-xl font-semibold py-1.5">
                                {{ currentDate.date }}
                            </span>
                            <span class="material-icons hover:bg-rose-500 text-rose-500 bg-gray-100 hover:text-white hover:shadow cursor-pointer w-6 h-6 flex items-center justify-center rounded-full">arrow_drop_down</span>
                        </div>
                        <div class="flex flex-col px-1 items-center">
                            <span class="material-icons hover:bg-rose-500 text-rose-500 bg-gray-100 hover:text-white hover:shadow cursor-pointer w-6 h-6 flex items-center justify-center rounded-full">arrow_drop_up</span>
                            <span class="text-xl font-semibold py-1.5">
                                {{ month[currentDate.month] }}
                            </span>
                            <span class="material-icons hover:bg-rose-500 text-rose-500 bg-gray-100 hover:text-white hover:shadow cursor-pointer w-6 h-6 flex items-center justify-center rounded-full">arrow_drop_down</span>
                        </div>
                        <div class="flex flex-col px-1 items-center">
                            <span class="material-icons hover:bg-rose-500 text-rose-500 bg-gray-100 hover:text-white hover:shadow cursor-pointer w-6 h-6 flex items-center justify-center rounded-full">arrow_drop_up</span>
                            <span class="text-xl font-semibold py-1.5">
                                {{ currentDate.year }}
                            </span>
                            <span class="material-icons hover:bg-rose-500 text-rose-500 bg-gray-100 hover:text-white hover:shadow cursor-pointer w-6 h-6 flex items-center justify-center rounded-full">arrow_drop_down</span>
                        </div>
                        
                    </div>
                </div>
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
            DayOfTheWeek: []
        }
    },
    computed: {
        currentDay() {
            return new Date(
                this.currentDate.year, this.currentDate.month, this.currentDate.date
            ).getDay()
        }
    },
    methods: {
        getCurrentDate() {
            let today = new Date()

            this.currentDate.date = today.getDate()
            this.currentDate.month = today.getMonth()
            this.currentDate.year = today.getFullYear()
        },
        getWeekday() {
            const weekday = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"]
            const d = new Date()
            let day = weekday[d.getDay()]

            // this.DaysOfTheWeek = day
            console.log(day)
        },
        getyear() {

            // const year = new Date().getFullYear(),
            // console.log(year)
        },
        getNumberOfDays() {
            const year = new Date().getFullYear()
            const month = new Date().getMonth()

            const NumDays = new Date(year, (month + 1), 0).getDate();
            console.log(`Month ${month + 1} has ${NumDays} days`)
        }
    },
    mounted() {
        this.getCurrentDate()
        this.getWeekday() 
        this.getNumberOfDays()      
    },
}
</script>

<style scoped>

</style>