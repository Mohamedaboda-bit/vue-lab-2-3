    <template>

    
    <div style="width:180vb;" class="d-flex flex-column ">
           <nav class="navbar navbar-expand-lg">
                <div class="container-fluid">
                    <a class="navbar-brand" href="#" @click.prevent="invisible=false">Books</a>
                        <div class="navbar-nav">                    
                            <button class="nav-link btn" @click="invisible=true">Show List</button>
                        </div>
                </div>
            </nav>


        <div class="d-flex flex-wrap justify-content p-2 mt-3 ">
            <div v-for="book in books" :key="book.ISBN" class="p-2" v-show="!invisible"> 
                <div class="card" style="width: 20rem; height:60rem;">
                <img :src="book.image" style="height: 40rem; width: 20rem;" class="card-img-top" alt="...">
                <div class="card-body">
                     <h5 class="card-title" :title="book.author">{{book.Name}}</h5>
                     <p class="card-text">{{book.description}}</p>
                 </div>
                <ul class="list-group list-group-flush">
                  <li class="list-group-item">category: {{ book.category }}</li>
                   <li class="list-group-item">author: {{ book.author }}</li>
                   <li class="list-group-item">price: {{ book.price }}</li>
                   <li class="list-group-item" :class="book.numberofpage <= 100 ? 'less' : 'more'">Pages: {{ book.numberofpage }}</li>
                 </ul>
                <div class="card-body">
                     <a href="#" class="btn " :class="book.show ? 'btn-secondary' : book.numberofpage <= 100 ? 'btn-info' : 'btn-primary'"  @click.prevent="Addbook(book)" :disabled="book.show">Add to list</a>
                 </div>
                </div>
            </div>
        </div>  


    <div class="row my-2 " v-show="invisible">
        <h3 v-show="cart.item.length==0">No books in the cart</h3>
        <table class="table table-bordered text-center "  v-show="cart.item.length>0">
            <thead>
                <tr>
                    <th>Name</th>
                    <th>Author</th>
                    <th>Price</th>
                    <th>Action</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="item in cart.item" :key="item.book.ISBN">
                    <td>{{ item.book.Name }}</td>
                    <td>{{ item.book.author }}</td>
                    <td>{{ formatPrice(item.book.price) }}</td>
                    <td>
                        <button class="btn btn-danger px-3 py-2 mx-2" @click="decreaseQuantity(item)">Delete</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
    
</div>

</template>


<script>
import books from "../../books.js"
export default{
    data:()=>({
        invisible:false,
        deletebook:false,
        books,
        cart:{
            item:[]
        }
    }),
    methods:{
        checkCard(book){
            return this.cart.item.some(item=> item.book.ISBN == book.ISBN)
        },
        formatPrice(price) {
            return new Intl.NumberFormat('en-US', {style: 'currency',currency: 'SAR'}).format(price);
        },
        increaseQuantity(item){
            item.quantity++;
        },
        decreaseQuantity(item){
            item.book.show=false;
            item.quantity--;
            if(item.quantity==0){
                this.cart.item.splice(this.cart.item.indexOf(item),1);
            }
        },
        Addbook(book) {
            if (!this.checkCard(book)) {
                book.show = true;
                this.cart.item.push({ book: book, quantity: 1 });
                }
        },
    }
}
</script>


