<template>
    <div class="bg-gray-100 min-h-screen flex justify-center items-center font-mono">
        <div class="bg-white p-8 h-[100%] rounded shadow">
            <div class="flex border-b py-2">
                <div> <span class="material-icons">face</span></div>
                <div>25 January, 2022</div>
                <div></div> 
            </div>
            <table class="shadow-inner my-4">
                <thead>
                    <tr class="">
                        <th class="px-2 py-1 shadow border">Sunday</th>
                        <th class="px-2 py-1 shadow border">Monday</th>
                        <th class="px-2 py-1 shadow border">Tuesday</th>
                        <th class="px-2 py-1 shadow border">Wednesday</th>
                        <th class="px-2 py-1 shadow border">Thursday</th>
                        <th class="px-2 py-1 shadow border">Friday</th>
                        <th class="px-2 py-1 shadow border">Saturday</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td class="border">1</td>
                        <td class="border">2</td>
                        <td class="border">3</td>
                        <td class="border">4</td>
                        <td class="border">5</td>
                        <td class="border">6</td>
                        <td class="border">7</td>
                    </tr>
                    <tr>
                        <td class="border">8</td>
                        <td class="border">9</td>
                        <td class="border">10</td>
                        <td class="border">11</td>
                        <td class="border">12</td>
                        <td class="border">13</td>
                        <td class="border">14</td>
                    </tr>
                    <tr>
                        <td class="border">15</td>
                        <td class="border">16</td>
                        <td class="border">17</td>
                        <td class="border">18</td>
                        <td class="border">19</td>
                        <td class="border">20</td>
                        <td class="border">21</td>
                    </tr>
                    <tr>
                        <td class="border">22</td>
                        <td class="border">23</td>
                        <td class="border">24</td>
                        <td class="border">25</td>
                        <td class="border">26</td>
                        <td class="border">27</td>
                        <td class="border">28</td>
                    </tr>
                    <tr>
                        <td class="border">29</td>
                        <td class="border">30</td>
                        <td class="border">31</td>
                        <td class="border">1</td>
                        <td class="border">2</td>
                        <td class="border">3</td>
                        <td class="border">4</td>
                    </tr>

                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            DaysOfTheWeek: [
                {title: "Sunday"},
                {title: "Sunday"},
                {title: "Sunday"},
                {title: "Sunday"},

            ]
        }
    },
    methods: {
        getWeekdays() {
            const weekday = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"]
            const d = new Date()
            let day = weekday[d.getDay()]

            // this.DaysOfTheWeek = day
            // console.log(this.DaysOfTheWeek)
        }
    },
    mounted() {
        this.getWeekdays()       
    },
}
</script>

<style scoped>

</style>