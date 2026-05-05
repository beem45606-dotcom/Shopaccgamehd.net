# Shopaccgamehd.net
// FULLSTACK SHOP ACC GAME (Frontend + Backend mock in one file for demo) // Run with: create-react-app or similar

import { useState } from "react";

export default function App() { const [accounts, setAccounts] = useState([ { id: 1, name: "Acc VIP", price: 50000, rank: "Kim Cương", status: "available" }, { id: 2, name: "Acc Pro", price: 100000, rank: "Thách Đấu", status: "available" } ]);

const [cart, setCart] = useState(null);

const buyAccount = (acc) => { setCart(acc); };

const confirmPayment = () => { setAccounts(accounts.map(acc => acc.id === cart.id ? { ...acc, status: "sold" } : acc)); alert("Thanh toán thành công! Acc sẽ được gửi cho bạn."); setCart(null); };

return ( <div className="p-6"> <h1 className="text-2xl font-bold mb-4">🔥 Shop Acc Free Fire</h1>

<div className="grid grid-cols-2 gap-4">
    {accounts.map(acc => (
      <div key={acc.id} className="border p-4 rounded-2xl shadow">
        <h2 className="text-xl">{acc.name}</h2>
        <p>Rank: {acc.rank}</p>
        <p>Giá: {acc.price}đ</p>
        <p className={acc.status === "sold" ? "text-red-500" : "text-green-500"}>
          {acc.status === "sold" ? "Đã bán" : "Còn"}
        </p>

        {acc.status === "available" && (
          <button
            className="bg-blue-500 text-white px-4 py-2 rounded mt-2"
            onClick={() => buyAccount(acc)}
          >
            Mua ngay
          </button>
        )}
      </div>
    ))}
  </div>

  {cart && (
    <div className="fixed bottom-0 left-0 right-0 bg-white p-4 border-t">
      <p>Đang mua: {cart.name}</p>
      <button
        className="bg-green-500 text-white px-4 py-2 rounded"
        onClick={confirmPayment}
      >
        Xác nhận thanh toán
      </button>
    </div>
  )}
</div>

); }
