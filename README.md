# WAKUBWA-TUU
Chagua mkoa wako ili upate pisikali ya mtaani kwako sasahivi uttombe
import React, { useState, useEffect } from "react";

export default function App() { const menuItems = ["Option 1", "Option 2", "Option 3"]; const [selectedIdx, setSelectedIdx] = useState(0); const [messages, setMessages] = useState(() => { const saved = localStorage.getItem("menu_messages"); return saved ? JSON.parse(saved) : menuItems.map(() => ""); }); const [input, setInput] = useState(messages[0] || "");

useEffect(() => { localStorage.setItem("menu_messages", JSON.stringify(messages)); }, [messages]);

function selectMenu(idx) { setSelectedIdx(idx); setInput(messages[idx] || ""); }

function saveMessage() { const newMessages = [...messages]; newMessages[selectedIdx] = input; setMessages(newMessages); alert("Ujumbe umehifadhiwa!"); }

function replayMessage() { setInput(messages[selectedIdx] || ""); alert("Ujumbe ume-replay!"); }

return ( <div style={{ fontFamily: "sans-serif", padding: 20 }}> <h1>Menu Replay App with LocalStorage</h1>

<div style={{ marginBottom: 20 }}>
    {menuItems.map((item, idx) => (
      <button
        key={idx}
        onClick={() => selectMenu(idx)}
        style={{
          marginRight: 8,
          marginBottom: 8,
          padding: "6px 12px",
          background: idx === selectedIdx ? "#111827" : "#fff",
          color: idx === selectedIdx ? "#fff" : "#111827",
          borderRadius: 6,
          border: "1px solid #ddd"
        }}
      >
        {item}
      </button>
    ))}
  </div>

  <div>
    <textarea
      value={input}
      onChange={(e) => setInput(e.target.value)}
      rows={5}
      style={{ width: "100%", padding: 8, borderRadius: 6, border: "1px solid #ddd" }}
      placeholder="Andika ujumbe hapa..."
    />
  </div>

  <div style={{ marginTop: 10 }}>
    <button onClick={saveMessage} style={{ padding: "6px 12px", borderRadius: 6 }}>
      Save
    </button>
    <button
      onClick={replayMessage}
      style={{ marginLeft: 8, padding: "6px 12px", borderRadius: 6 }}
    >
      Replay
    </button>
  </div>

  <div style={{ marginTop: 20 }}>
    <h4>Preview Messages:</h4>
    <ul>
      {menuItems.map((item, idx) => (
        <li key={idx}>
          <strong>{item}:</strong> {messages[idx] || "(no message)"}
        </li>
      ))}
    </ul>
  </div>
</div>

); }

