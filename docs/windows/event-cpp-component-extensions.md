---
title: události (rozšíření komponent C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event
- event_cpp
dev_langs:
- C++
helpviewer_keywords:
- event keyword [C++]
ms.assetid: c4998e42-883c-4419-bbf4-36cdc979dd27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7859b8b58bbd8765c38daea46efea5859ba61d67
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="event--c-component-extensions"></a>event (rozšíření komponent C++)
`event` Deklaruje – klíčové slovo *událostí*, který je registrovaný odběratelům oznámení (*obslužné rutiny událostí*), něco zájmu došlo k chybě.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 C + +/ CX podporuje deklarace *člena události* nebo *bloku událostí*. Člen události je sdružená vlastnost deklarace bloku událostí. Ve výchozím nastavení, deklaruje člen události `add()`, `remove()`, a `raise()` funkce, které jsou explicitně deklarované v bloku událostí. Přizpůsobení funkcí v události člen, místo toho deklarace bloku událostí a pak přepsat funkce, které požadujete.  
  
 **Syntaxe**  
  
```  
  
// event data member  
modifiereventdelegate^ event_name;     
  
// event block  
modifiereventdelegate^ event_name   
{  
   modifierreturn_valueadd(delegate^ name);  
   modifier void remove(delegate^ name);  
   modifier void raise(parameters);  
}  
```  
  
 **Parametry**  
  
 *Modifikátor*  
 Modifikátor, který lze použít v deklaraci události nebo metodu přístupového objektu události.  Možné hodnoty jsou `static` a `virtual`.  
  
 *delegate*  
 [Delegovat](../windows/delegate-cpp-component-extensions.md), jejichž podpis obslužné rutiny události se musí shodovat.  
  
 *EVENT_NAME*  
 Název události  
  
 *return_ value*  
 Vrácená hodnota metodu přístupového objektu události.  Chcete-li ověřit, musí být návratový typ `void`.  
  
 *Parametry*  
 (volitelné) Parametry `raise` metodu, která odpovídají podpis *delegovat* parametr.  
  
 **Poznámky**  
  
 Událost je přidružení mezi delegáta a členské funkce (obslužné rutiny události), který reaguje na aktivaci události a umožňuje klientům z libovolné třídy zaregistrovat metod, které v souladu s podpisem a návratový typ základní delegáta.  
  
 Existují dva typy deklarací události:  
  
 *událost – datový člen*  
 Kompilátor automaticky vytvoří úložiště pro událost v podobě člena typu delegáta a vytvoří interní `add()`, `remove()`, a `raise()` členské funkce. Člen data události musí být deklarován uvnitř třídy. Návratový typ návratového typu delegáta, musí odpovídat návratový typ obslužné rutiny události.  
  
 *událost bloku*  
 Blok událostí umožňuje explicitně deklarovat a přizpůsobit chování `add()`, `remove()`, a `raise()` metody.  
  
 Můžete použít `operators+=` a `operator-=` přidávat a odebírat událost obslužné rutiny nebo volání `add()` a `remove()` metody explicitně.  
  
 `event` je kontextové klíčové slovo; v tématu [klíčová slova Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md) Další informace.  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [událostí (C + +/ CX)](http://msdn.microsoft.com/library/windows/apps/hh755799.aspx).  
  
 Pokud chcete přidat a pak odeberte obslužné rutiny události, je nutné uložit EventRegistrationToken struktura, která je vrácená operací přidat. Pak v operaci odebrat, musíte použít strukturu uložené EventRegistrationToken k identifikaci obslužné rutiny události odeberou.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 `event` – Klíčové slovo umožňuje deklarovat událost. Událost je způsob, jak třídu zajistit oznámení, když něco týkající se stane.  
  
 **Syntaxe**  
  
```  
  
// event data member  
modifiereventdelegate^ event_name;   
  
// event block  
modifiereventdelegate^ event_name   
{  
   modifierreturn_valueadd(delegate^ name);  
   modifier void remove(delegate^ name);  
   modifier void raise(parameters);  
}  
```  
  
 **Parametry**  
  
 *Modifikátor*  
 Modifikátor, který lze použít v deklaraci události nebo metodu přístupového objektu události.  Možné hodnoty jsou `static` a `virtual`.  
  
 *delegate*  
 [Delegovat](../windows/delegate-cpp-component-extensions.md), jejichž podpis obslužné rutiny události se musí shodovat.  
  
 *EVENT_NAME*  
 Název události  
  
 *return_ value*  
 Vrácená hodnota metodu přístupového objektu události.  Chcete-li ověřit, musí být návratový typ `void`.  
  
 *Parametry*  
 (volitelné) Parametry `raise` metodu, která odpovídají podpis *delegovat* parametr.  
  
 **Poznámky**  
  
 Událost je přidružení mezi delegáta a členské funkce (obslužné rutiny události), který reaguje na aktivaci události a umožňuje klientům z libovolné třídy zaregistrovat metod, které v souladu s podpisem a návratový typ základní delegáta.  
  
 Delegát může mít jeden nebo více související metody, které se má volat při kódu označuje, že došlo k události. Událost v jednom programu můžete k dispozici další programy, které cílí common language runtime rozhraní .NET Framework.  
  
 Existují dva typy deklarací události:  
  
 *událost datové členy*  
 Úložiště pro událost v podobě člena typu delegáta, vytvoří se kompilátoru pro data člena události.  Člen data události musí být deklarován uvnitř třídy. Je také označován jako trivial události (viz následující ukázka kódu).  
  
 *bloky událostí*  
 Bloky událostí umožňují přizpůsobit chování přidat, odebrat a metody zvýšení implementací přidat, odebrat a vyvolat metody. Podpis přidat, odebrat a vyvolat metody se musí shodovat podpis delegáta.  Událost bloku události nejsou členy dat a jakékoli použití jako člena dat vygeneruje Chyba kompilátoru. 
  
 Návratový typ obslužné rutiny události musí shodovat s návratovým typem delegáta.  
  
 V rozhraní .NET Framework, lze považovat datový člen, jako by šlo metodu samotné (to znamená `Invoke` metoda jeho odpovídající delegáta). Typ delegáta musí předdefinovat deklarace člena spravovaných událostí. Naproti tomu metoda spravované události implicitně definuje odpovídající spravovaného delegáta Pokud již není definován.  Viz ukázka kódu na konci tohoto tématu pro příklad.  
  
 Když deklarace spravovaného událostí, můžete určit, přidávat a odebírat přístupové objekty, které se má volat při přidávání nebo odebírání obslužných rutin událostí pomocí += operátory a-=. Explicitně nelze volat metody přidat, odebrat a vygenerovat.  
  
 K vytvoření a používání událostí v jazyce Visual C++ musí být provedeny následující kroky:  
  
1.  Vytvořte nebo Identifikujte delegáta. Pokud definujete vlastní události, můžete musí také zkontrolujte, zda je delegáta pro použití s `event` – klíčové slovo. Pokud je předdefinovaná událost, v rozhraní .NET Framework například pak příjemci události potřebovat pouze znát název delegáta.  
  
2.  Vytvořte třídu, která obsahuje:  
  
    -   Události vytvořené z delegáta.  
  
    -   (volitelné) Metoda, která ověřuje, že instance delegáta deklarovat s `event` – klíčové slovo existuje. Tuto logiku, jinak hodnota musí být umístěny v kódu, který aktivuje událost.  
  
    -   Metody, které volají události. Tyto metody lze přepsání některé funkce základní třídy.  
  
     Tato třída definuje události.  
  
3.  Zadejte jednu nebo více tříd, které se připojují metody k události. Každá z těchto tříd přidružíte jednu nebo více metod událostí v základní třídě.  
  
4.  Událost použijte:  
  
    -   Vytvoření objektu třídy, která obsahuje deklaraci události.  
  
    -   Vytvoření objektu třídy, která obsahuje definici událostí.  
  
 Další informace o jazyce C + +/ CLI události, viz  
  
-   [Události v rozhraní](../dotnet/how-to-use-events-in-cpp-cli.md)  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující příklad kódu ukazuje deklarující páry delegáti, události a obslužné rutiny událostí; přihlášení k odběru (přidání) obslužné rutiny událostí; volání obslužných rutin událostí; a pak odhlášením (odebrání) obslužné rutiny událostí.  
  
```  
// mcppv2_events.cpp  
// compile with: /clr  
using namespace System;  
  
// declare delegates  
delegate void ClickEventHandler(int, double);  
delegate void DblClickEventHandler(String^);  
  
// class that defines events  
ref class EventSource {  
public:  
   event ClickEventHandler^ OnClick;   // declare the event OnClick  
   event DblClickEventHandler^ OnDblClick;   // declare OnDblClick  
  
   void FireEvents() {  
      // raises events  
      OnClick(7, 3.14159);  
      OnDblClick("Hello");  
   }  
};  
  
// class that defines methods that will called when event occurs  
ref class EventReceiver {  
public:  
   void OnMyClick(int i, double d) {  
      Console::WriteLine("OnClick: {0}, {1}", i, d);  
   }  
  
   void OnMyDblClick(String^ str) {  
      Console::WriteLine("OnDblClick: {0}", str);  
   }  
};  
  
int main() {  
   EventSource ^ MyEventSource = gcnew EventSource();  
   EventReceiver^ MyEventReceiver = gcnew EventReceiver();  
  
   // hook handler to event  
   MyEventSource->OnClick += gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);  
   MyEventSource->OnDblClick += gcnew DblClickEventHandler(MyEventReceiver, &EventReceiver::OnMyDblClick);  
  
   // invoke events  
   MyEventSource->FireEvents();  
  
   // unhook handler to event  
   MyEventSource->OnClick -= gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);  
   MyEventSource->OnDblClick -= gcnew DblClickEventHandler(MyEventReceiver, &EventReceiver::OnMyDblClick);  
}  
```  
  
 **Output**  
  
```Output  
OnClick: 7, 3.14159  
  
OnDblClick: Hello  
```  
  
 **Příklad**  
  
 Následující příklad kódu ukazuje logiku sloužící ke generování `raise` metoda trivial události: Pokud událost obsahuje jeden nebo více odběratele, volání `raise` metoda implicitně nebo explicitně vyvolá delegáta. Pokud delegát je návratový typ není `void` a pokud jsou odběratelé nulový počet událostí `raise` metoda vrátí výchozí hodnota pro typ delegáta. Pokud nejsou žádné události odběratele, volání `raise` metoda jednoduše vrátí a žádné došlo k výjimce. Pokud delegát vrátí typ není `void`, je vrácen typ delegáta.  
  
```  
// trivial_events.cpp  
// compile with: /clr /c  
using namespace System;  
public delegate int Del();  
public ref struct C {  
   int i;  
   event Del^ MyEvent;  
  
   void FireEvent() {  
      i = MyEvent();  
   }  
};  
  
ref struct EventReceiver {  
   int OnMyClick() { return 0; }  
};  
  
int main() {  
   C c;  
   c.i = 687;  
  
   c.FireEvent();  
   Console::WriteLine(c.i);  
   c.i = 688;  
  
   EventReceiver^ MyEventReceiver = gcnew EventReceiver();  
   c.MyEvent += gcnew Del(MyEventReceiver, &EventReceiver::OnMyClick);  
   Console::WriteLine(c.i);     
}  
```  
  
 **Output**  
  
```Output  
0  
  
688  
```  
  
## <a name="see-also"></a>Viz také  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)