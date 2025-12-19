https://github.com/prinkushwaha78907890-source/Prince-Kushwaha-.git# Prince-Kushwaha-
Its a Fintech platform where we can trade and investment in Shares, Bonds and it's has a AI assistant 
import React, { useState } from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button"; import { Input } from "@/components/ui/input"; import { Tabs, TabsContent, TabsList, TabsTrigger } from "@/components/ui/tabs"; import { MessageCircle, TrendingUp, ShieldCheck, UserCheck, AlertTriangle } from "lucide-react";

/* ---------------- LOGIN / KYC DEMO ---------------- */ const LoginKYC = () => { const [loggedIn, setLoggedIn] = useState(false);

if (loggedIn) { return ( <Card className="rounded-2xl shadow-md"> <CardContent className="p-4 space-y-2"> <h3 className="text-lg font-semibold">KYC Status</h3> <p className="text-green-600">✔ KYC Completed</p> </CardContent> </Card> ); }

return ( <Card className="rounded-2xl shadow-md"> <CardContent className="p-4 space-y-3"> <h3 className="text-lg font-semibold">Login / KYC</h3> <Input placeholder="Mobile / Email" /> <Input placeholder="PAN Number" /> <Button className="w-full" onClick={() => setLoggedIn(true)}> Verify & Login </Button> </CardContent> </Card> ); };

/* ---------------- BOND CARD ---------------- */ const BondCard = ({ name, yieldRate, minInvestment, rating }) => ( <Card className="rounded-2xl shadow-md"> <CardContent className="p-4 space-y-2"> <h3 className="text-lg font-semibold">{name}</h3> <p>Yield: <b>{yieldRate}%</b></p> <p>Min Investment: ₹{minInvestment}</p> <p>Rating: {rating}</p> <Button className="w-full mt-2">Invest</Button> </CardContent> </Card> );

/* ---------------- STOCK CARD ---------------- */ const StockCard = ({ name, price, change }) => ( <Card className="rounded-2xl shadow-md"> <CardContent className="p-4 space-y-2"> <h3 className="text-lg font-semibold">{name}</h3> <p>Price: ₹{price}</p> <p className={change >= 0 ? "text-green-600" : "text-red-600"}>{change}%</p> <Button className="w-full mt-2">Trade</Button> </CardContent> </Card> );

/* ---------------- AI RISK MANAGER ---------------- */ const AIRiskManager = () => ( <Card className="rounded-2xl shadow-md border-red-200"> <CardContent className="p-4 space-y-2"> <h3 className="text-lg font-semibold flex items-center gap-2"> <AlertTriangle className="text-red-500" /> AI Risk Manager </h3> <p className="text-sm">⚠ High exposure to NBFC bonds detected.</p> <p className="text-sm">✔ Suggestion: Diversify into Govt Bonds.</p> </CardContent> </Card> );

/* ---------------- AI CHATBOT ---------------- */ const Chatbot = () => { const [messages, setMessages] = useState([ { from: "bot", text: "Hi! I am your AI Wealth Assistant." } ]); const [input, setInput] = useState("");

const sendMessage = () => { if (!input) return; setMessages([ ...messages, { from: "user", text: input }, { from: "bot", text: "This is a demo AI response based on your portfolio." } ]); setInput(""); };

return ( <Card className="rounded-2xl shadow-lg"> <CardContent className="p-4"> <div className="h-48 overflow-y-auto space-y-2 mb-2"> {messages.map((m, i) => ( <div key={i} className={m.from === "user" ? "text-right" : "text-left"}> <span className="inline-block px-3 py-1 rounded-xl bg-gray-100">{m.text}</span> </div> ))} </div> <div className="flex gap-2"> <Input value={input} onChange={(e) => setInput(e.target.value)} placeholder="Ask about stocks, bonds, risk..." /> <Button onClick={sendMessage}><MessageCircle /></Button> </div> </CardContent> </Card> ); };

/* ---------------- MAIN PLATFORM ---------------- */ export default function SecureWealthDemo() { return ( <div className="p-6 space-y-8"> <h1 className="text-3xl font-bold">Secure Wealth – Fintech Demo Platform</h1>

<Tabs defaultValue="login">
    <TabsList>
      <TabsTrigger value="login">Login / KYC</TabsTrigger>
      <TabsTrigger value="bonds">Bonds</TabsTrigger>
      <TabsTrigger value="stocks">Stocks</TabsTrigger>
      <TabsTrigger value="risk">AI Risk</TabsTrigger>
      <TabsTrigger value="ai">AI Chatbot</TabsTrigger>
    </TabsList>

    <TabsContent value="login"><LoginKYC /></TabsContent>

    <TabsContent value="bonds">
      <div className="grid md:grid-cols-3 gap-4">
        <BondCard name="AAA Corporate Bond" yieldRate={9.5} minInvestment={10000} rating="AAA" />
        <BondCard name="Govt Bond 2030" yieldRate={7.2} minInvestment={5000} rating="Sovereign" />
        <BondCard name="NBFC Bond" yieldRate={10.8} minInvestment={20000} rating="AA" />
      </div>
    </TabsContent>

    <TabsContent value="stocks">
      <div className="grid md:grid-cols-3 gap-4">
        <StockCard name="Reliance" price={2480} change={1.2} />
        <StockCard name="TCS" price={3560} change={-0.6} />
        <StockCard name="HDFC Bank" price={1490} change={0.8} />
      </div>
    </TabsContent>

    <TabsContent value="risk"><AIRiskManager /></TabsContent>
    <TabsContent value="ai"><Chatbot /></TabsContent>
  </Tabs>
</div>

); }
