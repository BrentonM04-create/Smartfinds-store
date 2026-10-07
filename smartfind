const products=[
{id:1,name:"Magnetic Cable Organizer",cat:"Desk",price:18.99,emoji:"🧲",desc:"Keep charging cables exactly where you need them."},
{id:2,name:"Pocket Tool Keychain",cat:"Everyday",price:14.99,emoji:"🛠️",desc:"A compact set of useful tools for everyday fixes."},
{id:3,name:"Motion Sensor Night Light",cat:"Home",price:22.99,emoji:"💡",desc:"Soft automatic lighting for halls, closets, and stairs."},
{id:4,name:"Leakproof Travel Case",cat:"Travel",price:19.99,emoji:"🧳",desc:"A tidy, water-resistant home for small essentials."},
{id:5,name:"Adjustable Phone Stand",cat:"Desk",price:16.99,emoji:"📱",desc:"A sturdy viewing angle for calls, videos, and recipes."},
{id:6,name:"Portable Cleaning Brush",cat:"Home",price:12.99,emoji:"🧽",desc:"A compact detail brush for hard-to-reach spaces."},
{id:7,name:"Car Seat Gap Organizer",cat:"Auto",price:24.99,emoji:"🚗",desc:"Turn the awkward space beside your seat into storage."},
{id:8,name:"Rechargeable Mini Fan",cat:"Everyday",price:27.99,emoji:"🌬️",desc:"Compact airflow for desks, travel, and warm days."}
];
let cart=JSON.parse(localStorage.getItem("sf_cart")||"[]");
const cats=["All",...new Set(products.map(p=>p.cat))];
function renderFilters(){filters.innerHTML=cats.map((c,i)=>`<button class="${i===0?'active':''}" onclick="filter('${c}',this)">${c}</button>`).join("")}
function render(list=products){productsEl.innerHTML=list.map(p=>`<article class="product"><div class="pic">${p.emoji}</div><div class="body"><span class="tag">${p.cat}</span><h3>${p.name}</h3><p>${p.desc}</p><div class="buy"><b>$${p.price.toFixed(2)}</b><button onclick="add(${p.id})">Add</button></div></div></article>`).join("")}
function filter(cat,el){document.querySelectorAll(".filters button").forEach(x=>x.classList.remove("active"));el.classList.add("active");render(cat==="All"?products:products.filter(p=>p.cat===cat))}
function add(id){cart.push(id);save();openCart()}
function addHero(){add(1)}
function save(){localStorage.setItem("sf_cart",JSON.stringify(cart));updateCart()}
function updateCart(){cartCount.textContent=cart.length;let rows=cart.map((id,i)=>products.find(p=>p.id===id));cartItems.innerHTML=rows.length?rows.map((p,i)=>`<div class="cartRow"><div class="emoji">${p.emoji}</div><div><b>${p.name}</b><div>$${p.price.toFixed(2)}</div><div class="qty"><button onclick="removeOne(${i})">−</button><small>1</small><button onclick="add(${p.id})">+</button></div></div></div>`).join(""):`<p>Your cart is empty.</p>`;total.textContent="$"+rows.reduce((s,p)=>s+p.price,0).toFixed(2)}
function removeOne(i){cart.splice(i,1);save()}
function openCart(){overlay.classList.add("open");updateCart()}
function closeCart(e){if(!e||e.target===overlay)overlay.classList.remove("open")}
function checkout(){alert("Demo checkout: connect Stripe, Shopify, or another payment provider to accept live payments.")}
function runAI(){aiResult.textContent=" Scan complete — 8 products reviewed; 3 merchandising opportunities found."}
const productsEl=document.getElementById("products"),filters=document.getElementById("filters"),cartCount=document.getElementById("cartCount"),overlay=document.getElementById("overlay"),cartItems=document.getElementById("cartItems"),total=document.getElementById("total"),aiResult=document.getElementById("aiResult");
renderFilters();render();updateCart();