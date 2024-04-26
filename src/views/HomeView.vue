<script>
import inputBtnView from "@/components/inputBtnView.vue";
import { usershopCart } from "@/stores/shoppingCart";
import { mapState, mapActions } from "pinia";
export default {
  components: {
    inputBtnView,
  },

  data() {
    return {
      currentView: "table",
      card: {},
      productdataArr:
        [{ "id": 1, "name": "Bytecard", "pic": " https://fakeimg.pl/300/", "description": "Immunization not carried out because of caregiver refusal", "price": 954, "quantity": 1 },
        { "id": 2, "name": "Alphazap", "pic": " https://fakeimg.pl/300/", "description": "Unspecified symptoms and signs involving cognitive functions following other cerebrovascular disease", "price": 776, "quantity": 1 },
        { "id": 3, "name": "Ronstring", "pic": " https://fakeimg.pl/300/", "description": "Unspecified fracture of shaft of unspecified tibia, initial encounter for open fracture type I or II", "price": 670, "quantity": 1 },
        { "id": 4, "name": "Bitchip", "pic": " https://fakeimg.pl/300/", "description": "Displaced fracture of coracoid process, right shoulder, subsequent encounter for fracture with delayed healing", "price": 346, "quantity": 1 },
        { "id": 5, "name": "Andalax", "pic": " https://fakeimg.pl/300/", "description": "Nondisplaced oblique fracture of shaft of left radius, sequela", "price": 515, "quantity": 1 },
        { "id": 6, "name": "Hatity", "pic": " https://fakeimg.pl/300/", "description": "Dislocation of L4/L5 lumbar vertebra, subsequent encounter", "price": 707, "quantity": 1 },
        { "id": 7, "name": "Ronstring", "pic": " https://fakeimg.pl/300/", "description": "Unspecified fracture of upper end of right radius, subsequent encounter for closed fracture with delayed healing", "price": 640, "quantity": 1 },
        { "id": 8, "name": "Konklab", "pic": " https://fakeimg.pl/300/", "description": "Partial physeal arrest, left proximal humerus", "price": 534, "quantity": 1 },
        { "id": 9, "name": "Lotlux", "pic": " https://fakeimg.pl/300/", "description": "Contracture, unspecified shoulder", "price": 705, "quantity": 1 },
        { "id": 10, "name": "Aerified", "pic": " https://fakeimg.pl/300/", "description": "Other disorders of vitreous body", "price": 826, "quantity": 1 },
        { "id": 11, "name": "Bamity", "pic": " https://fakeimg.pl/300/", "description": "Mechanical complication of coronary artery bypass graft and biological heart valve graft", "price": 651, "quantity": 1 },
        { "id": 12, "name": "Bigtax", "pic": " https://fakeimg.pl/300/", "description": "Other mechanical complication of carotid arterial graft (bypass), sequela", "price": 851, "quantity": 1 },
        { "id": 13, "name": "Domainer", "pic": " https://fakeimg.pl/300/", "description": "Other osteoporosis with current pathological fracture, right shoulder, sequela", "price": 418, "quantity": 1 },
        { "id": 14, "name": "Tresom", "pic": " https://fakeimg.pl/300/", "description": "Exposure to reduction in atmospheric pressure while surfacing from underground, initial encounter", "price": 754, "quantity": 1 },
        { "id": 15, "name": "Duobam", "pic": " https://fakeimg.pl/300/", "description": "Displaced unspecified fracture of left great toe, initial encounter for closed fracture", "price": 7686, "quantity": 1 },
        { "id": 16, "name": "Duobam", "pic": " https://fakeimg.pl/300/", "description": "Mixed cellularity Hodgkin lymphoma, spleen", "price": 788, "quantity": 1 },
        { "id": 17, "name": "Lotstring", "pic": " https://fakeimg.pl/300/", "description": "Lead-induced gout, unspecified site", "price": 3115, "quantity": 1 },
        { "id": 18, "name": "Tres-Zap", "pic": " https://fakeimg.pl/300/", "description": "Complete traumatic transphalangeal amputation of other and unspecified finger(s)", "price": 2734, "quantity": 1 },
        { "id": 19, "name": "Zaam-Dox", "pic": " https://fakeimg.pl/300/", "description": "Nondisplaced segmental fracture of shaft of right femur", "price": 415, "quantity": 1 },
        { "id": 20, "name": "Voyatouch", "pic": " https://fakeimg.pl/300/", "description": "Other fracture of shaft of left ulna, subsequent encounter for closed fracture with routine healing", "price": 398, "quantity": 1 }],
    };
  },

  computed: {
    ...mapState(usershopCart, ["cartData"]),
  },

  // async mounted() {
  //   try {
  //     const product = await fetch("./MOCK_DATA.json");
  //     const data = await product.json();
  //     this.productdataArr = data;
  //   } catch (error) {
  //     console.error(error);
  //   }
  // },

  methods: {
    toggleView(view) {
      this.currentView = view;
    },

    ...mapActions(usershopCart, ["addCart"]),
  },
};
</script>

<template>
  <div>
    <div class="title-div mt-5 ml-3 mb-5 flex">
      <h1 class="text-3xl font-bold">商品清單列表</h1>
    </div>
    <div class="flex gap-3 justify-end px-3 mb-3">
      <i @click="toggleView('table')" class="fa-solid fa-table-cells-large"></i>
      <i @click="toggleView('list')" class="fa-solid fa-list"></i>
    </div>
    <div v-if="currentView === 'table'" class="div">
      <div class="flex flex-wrap w-11/12 m-auto gap-4 justify-center">
        <div v-for="item in productdataArr" :key="item.id"
          class="w-1/6 min-w-[150px] min-h-[500px] flex flex-col rounded-xl border overflow-hidden">
          <img src="../img/下載.png" alt="" />
          <div class="md-5">
            <h2 class="my-4">商品名稱:{{ item.name }}</h2>
            <p class="my-4 break-words">商品介紹:{{ item.description }}</p>
            <p class="my-5">商品價格:{{ item.price }}</p>
          </div>
          <div class="flex-grow"></div>
          <div class="flex">
            <div>數量：</div>
            <inputBtnView @update="(newValue) => {
        item.quantity = newValue;
      }
        " :quantity="item.quantity"></inputBtnView>
          </div>
          <button @click="addCart(item)" type="button" class="text-center bg-slate-500 text-white mt-3"><i
              class="fa-solid fa-cart-shopping relative"></i>加入購物車</button>
        </div>
      </div>
    </div>
    <div v-if="currentView === 'list'" class="table-container mb-6 px-5">
      <div class="grid-table">
        <div class="grid-thead">
          <div class="grid-top grid-cols-6 grid border-y font-bold gap-x-3">
            <div class="grid-th text-center">商品圖片</div>
            <div class="grid-th text-center">商品名稱</div>
            <div class="grid-th">產品描述</div>
            <div class="grid-th text-center">價錢</div>
            <div class="grid-th opacity-0"></div>
          </div>
        </div>
        <div class="grid-tbody">
          <div v-for="item in productdataArr" :key="item.id"
            class="grid-tr grid-cols-6 grid border-b min-h-[80px] gap-x-3">
            <div class="flex justify-center items-center">
              <img src="../img/下載.png" alt="" class="h-[100px] w-[100px]" />
            </div>
            <div class="flex justify-center items-center">
              <h2 class="my-4">{{ item.name }}</h2>
            </div>
            <div class="flex justify-center items-center">
              <p class="my-4 break-words">{{ item.description }}</p>
            </div>
            <div class="flex justify-center">
              <p class="my-5">{{ item.price }}</p>
            </div>
            <div class="grid-td flex justify-center items-center">
              <div class="flex flex-col">
                <inputBtnView @update="(newValue) => {
        item.quantity = newValue;
      }
        " :quantity="item.quantity"></inputBtnView>
                <button type="button" @click="addCart(item)"
                  class="text-center bg-slate-500 text-white mt-3 w-[180px]"><i
                    class="fa-solid fa-cart-shopping relative"></i>加入購物車</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<style scoped></style>
