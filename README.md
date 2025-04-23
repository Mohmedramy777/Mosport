# Mosport
import { useState } from 'react'; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button";

const products = [ { id: 1, name: "حذاء رياضي نايك", price: 1200, image: "https://via.placeholder.com/200x200.png?text=Nike+Shoe", category: "أحذية", }, { id: 2, name: "تيشيرت أديداس", price: 650, image: "https://via.placeholder.com/200x200.png?text=Adidas+Shirt", category: "ملابس", }, { id: 3, name: "كرة قدم Puma", price: 300, image: "https://via.placeholder.com/200x200.png?text=Puma+Ball", category: "معدات", }, ];

export default function SportyStore() { const [cart, setCart] = useState([]);

const addToCart = (product) => { setCart([...cart, product]); };

return ( <div className="p-6 max-w-7xl mx-auto"> <h1 className="text-3xl font-bold mb-6 text-center">متجر SportyStore</h1>

<div className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6">
    {products.map((product) => (
      <Card key={product.id} className="rounded-2xl shadow-lg">
        <CardContent className="p-4">
          <img src={product.image} alt={product.name} className="w-full rounded-xl mb-4" />
          <h2 className="text-xl font-semibold mb-2">{product.name}</h2>
          <p className="text-gray-700 mb-2">الفئة: {product.category}</p>
          <p className="text-green-600 font-bold mb-4">{product.price} ج.م</p>
          <Button onClick={() => addToCart(product)} className="w-full">أضف إلى السلة</Button>
        </CardContent>
      </Card>
    ))}
  </div>

  <div className="mt-10">
    <h2 className="text-2xl font-bold mb-4">السلة ({cart.length})</h2>
    {cart.length === 0 ? (
      <p className="text-gray-500">لا توجد عناصر في السلة بعد.</p>
    ) : (
      <ul className="space-y-2">
        {cart.map((item, index) => (
          <li key={index} className="border p-3 rounded-xl bg-gray-50">
            {item.name} - {item.price} ج.م
          </li>
        ))}
      </ul>
    )}
  </div>
</div>

); }

