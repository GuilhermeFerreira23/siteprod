import React from "react";
import { motion } from "framer-motion";
import { ArrowRight, Clock, MapPin, ShieldCheck, PhoneCall, PackageSearch, Truck, CheckCircle2 } from "lucide-react";
import { Button } from "@/components/ui/button";
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";

// ⚙️ COMO USAR
// 1) Substitua WHATSAPP_NUMBER pelo seu número no formato 55DDDNÚMERO (ex.: 5519999999999)
// 2) Ajuste preços/faixas na seção Preços
// 3) Publique em qualquer ambiente React/Vite/Next. Com Tailwind + shadcn/ui instalados fica pronto.
// 4) A página é "one screen" + modais/ancoras rápidas.

const WHATSAPP_NUMBER = "5519993309230"; // TODO: troque aqui

const features = [
  {
    icon: <Clock className="w-6 h-6" />,
    title: "SLA 2h/4h garantido",
    desc: "Corridas urbanas Indaiatuba em até 2h. RMC/ Viracopos em até 4h.",
  },
  {
    icon: <MapPin className="w-6 h-6" />,
    title: "Janelas Viracopos",
    desc: "Saídas programadas diárias para o aeroporto e EADIs da região.",
  },
  {
    icon: <ShieldCheck className="w-6 h-6" />,
    title: "Rastreamento simples",
    desc: "Status por WhatsApp + comprovante de entrega (foto/assinatura).",
  },
  {
    icon: <Truck className="w-6 h-6" />,
    title: "Motos + Carro sob demanda",
    desc: "Escolha por urgência, volume e raio. Parcerias homologadas.",
  },
];

const priceRows = [
  { faixa: "Urbano Indaiatuba (até 6 km)", preco: "R$ 35 + R$ 3,50/km", sla: "até 2h" },
  { faixa: "Indaiatuba ⇄ Viracopos", preco: "a partir de R$ 120", sla: "até 4h" },
  { faixa: "RMC (Campinas, Valinhos, etc.)", preco: "R$ 3,80/km", sla: "até 4h" },
  { faixa: "Janela Programada (diária)", preco: "pacotes sob consulta", sla: "fixo" },
];

export default function LandingCourierIndaiatuba() {
  return (
    <div className="min-h-screen w-full bg-gradient-to-b from-white to-slate-50 text-slate-900">
      {/* NAV */}
      <header className="sticky top-0 z-40 backdrop-blur bg-white/70 border-b">
        <div className="max-w-6xl mx-auto px-4 py-3 flex items-center justify-between">
          <div className="flex items-center gap-2">
            <Truck className="w-6 h-6" />
            <span className="font-semibold">HotShot Indaiatuba</span>
          </div>
          <div className="hidden md:flex items-center gap-2">
            <a href="#precos" className="text-sm hover:underline">Preços</a>
            <a href="#como-funciona" className="text-sm hover:underline">Como funciona</a>
            <a href="#faq" className="text-sm hover:underline">FAQ</a>
            <Button asChild className="rounded-2xl">
              <a
                href={`https://wa.me/${5519991427379}?text=Olá!%20Quero%20cotar%20uma%20corrida%20expressa.`}
                target="_blank"
                rel="noreferrer"
              >
                Falar no WhatsApp
              </a>
            </Button>
          </div>
        </div>
      </header>

      {/* HERO */}
      <section className="max-w-6xl mx-auto px-4 py-10 md:py-16">
        <div className="grid md:grid-cols-2 gap-8 items-center">
          <motion.div initial={{ opacity: 0, y: 10 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 0.5 }}>
            <h1 className="text-3xl md:text-5xl font-extrabold leading-tight">
              Entregas B2B <span className="text-slate-600">Indaiatuba ⇄ Viracopos ⇄ RMC</span> em até 2h/4h
            </h1>
            <p className="mt-4 text-lg text-slate-700">
              Corridas urgentes para peças, amostras, documentos aduaneiros e itens críticos. Rastreamento simples via
              WhatsApp e janelas programadas para Viracopos.
            </p>
            <div className="mt-6 flex flex-col sm:flex-row gap-3">
              <Button asChild size="lg" className="rounded-2xl">
                <a
                  href={`https://wa.me/${5519991427379}?text=Olá!%20Preciso%20de%20uma%20coleta%20agora%20em%20Indaiatuba.`}
                  target="_blank"
                  rel="noreferrer"
                >
                  Solicitar corrida agora
                  <ArrowRight className="ml-2 w-4 h-4" />
                </a>
              </Button>
              <Button variant="secondary" asChild size="lg" className="rounded-2xl">
                <a href="#precos">Ver faixas de preço</a>
              </Button>
            </div>
            <div className="mt-6 flex items-center gap-3 text-sm text-slate-600">
              <ShieldCheck className="w-4 h-4" /> SLA garantido • Comprovante de entrega • Nota fiscal
            </div>
          </motion.div>

          <motion.div initial={{ opacity: 0, y: 10 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 0.6 }}>
            <Card className="rounded-2xl shadow-lg">
              <CardHeader>
                <CardTitle className="flex items-center gap-2"><PackageSearch className="w-5 h-5"/>Cotação rápida</CardTitle>
              </CardHeader>
              <CardContent>
                <form className="grid grid-cols-1 md:grid-cols-2 gap-3">
                  <input className="border rounded-xl px-3 py-2" placeholder="Origem (bairro/empresa)" />
                  <input className="border rounded-xl px-3 py-2" placeholder="Destino (bairro/empresa)" />
                  <input className="border rounded-xl px-3 py-2" placeholder="Tipo (peça/doc/amostra)" />
                  <input className="border rounded-xl px-3 py-2" placeholder="Peso/Volume aprox." />
                  <input className="border rounded-xl px-3 py-2 md:col-span-2" placeholder="Contato (nome e tel.)" />
                  <Button asChild className="rounded-2xl md:col-span-2">
                    <a
                      href={`https://wa.me/${5519991427379}?text=Olá!%20Quero%20cotação%20para:%20[preencha%20os%20campos%20e%20envie]`}
                      target="_blank"
                      rel="noreferrer"
                    >
                      Enviar por WhatsApp
                    </a>
                  </Button>
                  <p className="text-xs text-slate-500 md:col-span-2 flex items-center gap-1 mt-1">
                    <PhoneCall className="w-3 h-3"/> Atendimento 07h–19h (plantão sob demanda)
                  </p>
                </form>
              </CardContent>
            </Card>
          </motion.div>
        </div>
      </section>

      {/* FEATURES */}
      <section id="como-funciona" className="max-w-6xl mx-auto px-4 pb-6">
        <div className="grid sm:grid-cols-2 lg:grid-cols-4 gap-4">
          {features.map((f, i) => (
            <Card key={i} className="rounded-2xl">
              <CardContent className="p-5">
                <div className="flex items-center gap-3 mb-2">{f.icon}<h3 className="font-semibold">{f.title}</h3></div>
                <p className="text-sm text-slate-600">{f.desc}</p>
              </CardContent>
            </Card>
          ))}
        </div>
      </section>

      {/* PRICES */}
      <section id="precos" className="max-w-6xl mx-auto px-4 py-8">
        <Card className="rounded-2xl">
          <CardHeader>
            <CardTitle>Tabela simples de preços</CardTitle>
          </CardHeader>
          <CardContent>
            <div className="overflow-x-auto">
              <table className="min-w-full text-sm">
                <thead>
                  <tr className="text-left border-b">
                    <th className="py-2 pr-6">Faixa</th>
                    <th className="py-2 pr-6">Preço base</th>
                    <th className="py-2">SLA</th>
                  </tr>
                </thead>
                <tbody>
                  {priceRows.map((r, idx) => (
                    <tr key={idx} className="border-b last:border-0">
                      <td className="py-3 pr-6">{r.faixa}</td>
                      <td className="py-3 pr-6 font-medium">{r.preco}</td>
                      <td className="py-3">{r.sla}</td>
                    </tr>
                  ))}
                </tbody>
              </table>
            </div>
            <div className="mt-4 text-xs text-slate-500">
              * Valores estimativos. Pedágios/espera/retorno podem ser cobrados à parte. Emitimos NF-e.
            </div>
          </CardContent>
        </Card>
      </section>

      {/* TRUST + DEPOIMENTOS (placeholders para pilotos) */}
      <section className="max-w-6xl mx-auto px-4 py-6">
        <div className="grid md:grid-cols-3 gap-4">
          {[
            { name: "Indústria A", text: "Entrega de amostras em 1h55, salvou nossa linha." },
            { name: "Operador Logístico B", text: "Janela Viracopos diária trouxe previsibilidade." },
            { name: "Clínica C", text: "Documentos sensíveis com cuidado e agilidade." },
          ].map((d, i) => (
            <Card key={i} className="rounded-2xl">
              <CardContent className="p-5">
                <p className="text-sm">“{d.text}”</p>
                <div className="mt-3 text-xs text-slate-500">— {d.name}</div>
              </CardContent>
            </Card>
          ))}
        </div>
      </section>

      {/* CTA FINAL */}
      <section className="max-w-6xl mx-auto px-4 pb-12">
        <Card className="rounded-2xl">
          <CardContent className="p-6 flex flex-col md:flex-row items-start md:items-center justify-between gap-4">
            <div className="flex items-start gap-3">
              <CheckCircle2 className="w-6 h-6 mt-1"/>
              <div>
                <h3 className="font-semibold text-lg">Pronto para testar por 7 dias?</h3>
                <p className="text-sm text-slate-600">Sem burocracia: você solicita, nós coletamos e entregamos com SLA. Um canal direto no WhatsApp.</p>
              </div>
            </div>
            <Button asChild size="lg" className="rounded-2xl">
              <a
                href={`https://wa.me/${5519991427379}?text=Quero%20testar%207%20dias%20de%20corridas%20expressas.`}
                target="_blank"
                rel="noreferrer"
              >
                Iniciar teste
                <ArrowRight className="ml-2 w-4 h-4" />
              </a>
            </Button>
          </CardContent>
        </Card>
      </section>

      {/* FOOTER */}
      <footer className="border-t">
        <div className="max-w-6xl mx-auto px-4 py-6 text-xs text-slate-500 flex flex-col md:flex-row gap-2 md:gap-6 md:items-center md:justify-between">
          <div>© {new Date().getFullYear()} HotShot Indaiatuba • MEI • Alvará/Motofrete regularizados.</div>
          <div className="flex items-center gap-4">
            <a href="#faq" className="hover:underline">FAQ</a>
            <a href={`tel:+${5519991427379}`} className="hover:underline">Telefone</a>
            <a href={`https://wa.me/${5519991427379}`} target="_blank" rel="noreferrer" className="hover:underline">WhatsApp</a>
          </div>
        </div>
      </footer>
    </div>
  );
}
