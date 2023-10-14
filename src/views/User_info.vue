<template>
    <div class="container mt-5">
        <div class="row justify-content-center">
            <div class="col-md-6">
                <div class="card">
                    <div class="card-body">
                        <br>
                        <h2 class="card-title text-center mb-4">Your Information</h2>
                        <form @submit.prevent="submitForm" @keydown.enter.prevent="">
                            <h6>CONTACT</h6>
                            <div class="input-group">
                                <div class="underlined-input-container">
                                    <input id="Name_Last" v-model="name" class="underlined-input"
                                        placeholder="ชื่อ-นามสกุล" />
                                </div>
                            </div>
                            <div class="input-group">
                                <div class="underlined-input-container">
                                    <input id="Phone" v-model="phone" class="underlined-input"
                                        placeholder="เบอร์โทร" />
                                </div>
                            </div>
                            <h6>ADDRESS</h6>
                            <div class="input-group">
                                <div class="underlined-input-container">
                                    <input id="จังหวัด" v-model="province" class="underlined-input"
                                        placeholder="จังหวัด" />
                                </div>
                            </div>
                            <div class="input-group">
                                <div class="underlined-input-container">
                                    <input id="อำเภอ" v-model="district" class="underlined-input" placeholder="อำเภอ" />
                                </div>
                            </div>
                            <div class="input-group">
                                <div class="underlined-input-container">
                                    <input id="postal_code" v-model="postalCode" class="underlined-input"
                                        placeholder="รหัสไปรษณีย์" />
                                </div>
                            </div>
                            <div class="input-group">
                                <div class="underlined-input-container">
                                    <input id="email" v-model="email" class="underlined-input"
                                        placeholder="E-mail" />
                                </div>
                            </div>
                            <div class="input-group">
                                <div class="underlined-input-container">
                                    <input id="more_detail" v-model="moreDetail" class="underlined-input"
                                        placeholder="เพิ่มเติม" />
                                </div>
                            </div>
                            <br>
                            <button type="submit" class="btn btn-primary w-100"
                            :disabled="isSubmitDisabled">ยืนยันข้อมูล</button>
                        <br><br><br>
                    </form>
                </div>
            </div>
        </div>
    </div>
</div>
<br>
</template>

<script>
export default {
    data() {
        return {
            name: "",
            phone: "",
            province: "",
            district: "",
            postalCode: "",
            email: "",
            moreDetail: "",
        };
    },
    computed: {
    isSubmitDisabled() {
        return !(
            this.name.trim() &&
            this.phone.trim() &&
            this.province.trim() &&
            this.district.trim() &&
            this.postalCode.trim() &&
            this.email.trim() &&
            this.moreDetail.trim()
            );
        },
    },
    methods: {
        submitForm() {
            this.name = this.name.trim();
            this.phone = this.phone.trim();
            this.province = this.province.trim();
            this.district = this.district.trim();
            this.postalCode = this.postalCode.trim();
            this.email = this.email.trim();
            this.moreDetail = this.moreDetail.trim();

            console.log('Name:', this.name);
            console.log('Phone:', this.phone);
            console.log('Province:', this.province);
            console.log('District:', this.district);
            console.log('Postal Code:', this.postalCode);
            console.log('Email:', this.email);
            console.log('More Detail:', this.moreDetail);
  // ใช้ Vue Router เพื่อไปยังหน้าปลายทางพร้อมกับข้อมูลเป็นพารามิเตอร์เส้นทาง
            this.$router.push({
                name: 'OrderHistory',
                params: {
                    name: this.name,
                    phone: this.phone,
                    province: this.province,
                    district: this.district,
                    postalCode: this.postalCode,
                    email: this.email,
                    moreDetail: this.moreDetail
                    }
                });
            }

        }

    };
</script>

<style scoped>
.input-group {
    position: relative;
    margin-bottom: 20px;
}

.input-label {
    position: absolute;
    top: -20px;
    left: 0;
    font-size: 14px;
    color: #777;
}

.underlined-input-container {
    position: relative;
    width: 100%;
    margin-bottom: 10px;
}

.underlined-input {
    width: 100%;
    border: none;
    border-bottom: 1px solid #ccc;
    font-size: 16px;
    padding: 10px 10px 10px 20px;
    background-color: transparent;
    outline: none;
}

.underlined-input:focus {
    border-bottom: 2px solid #007bff;
}

.card {
    border-radius: 15px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.card-title {
    font-size: 24px;
}

.form-label {
    font-weight: bold;
}

.btn-primary {
    background-color: #007bff;
    border-color: #007bff;
}

.btn-primary:hover {
    background-color: #0056b3;
    border-color: #0056b3;
}
</style>