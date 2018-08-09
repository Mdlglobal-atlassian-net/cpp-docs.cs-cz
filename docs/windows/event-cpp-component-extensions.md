---
title: Event (rozšíření komponent C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 6b3ee48394eede37873ce074c275290307215815
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649133"
---
# <a name="event--c-component-extensions"></a>event (rozšíření komponent C++)
**Události** deklaruje klíčové slovo *události*, který je registrovaný odběratelům oznámení (*obslužné rutiny událostí*), která něco zájmu došlo k chybě.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 C + +/ CX podporuje deklarace *člen události* nebo *bloku událostí*. Člen události představuje zkratku pro deklarování blok události. Ve výchozím nastavení, deklaruje člen události `add()`, `remove()`, a `raise()` funkce, které jsou explicitně deklarované v bloku události. K přizpůsobení funkcí v člen události, místo toho Deklarujte blok události a pak přepsání funkce, které budete potřebovat.  
  
### <a name="syntax"></a>Syntaxe
  
```cpp  
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
  
### <a name="parameters"></a>Parametry
 *Modifikátor*  
 Modifikátor, který lze použít v deklaraci události nebo metodu přistupujícího objektu události.  Možné hodnoty jsou **statické** a **virtuální**.  
  
 *delegate*  
 [Delegovat](../windows/delegate-cpp-component-extensions.md), jehož předpis obslužná rutina události se musí shodovat.  
  
 *EVENT_NAME*  
 Název události  
  
 *return_ value*  
 Na návratový typ metody přistupujícího objektu události.  Chcete-li ověřit, návratový typ musí být **void**.  
  
 *Parametry*  
 (volitelné) Parametry pro `raise` metodu, která odpovídá podpisu *delegovat* parametru.  
  
### <a name="remarks"></a>Poznámky
  
 Událost je přidružení mezi delegáta a členské funkce (Obslužná rutina události), který reaguje na aktivaci události a umožňuje klientům z jiné třídy, metody, které v souladu s podpisem a návratový typ delegáta základní registrace.  
  
 Existují dva typy deklarací události:  
  
 *datový člen události*  
 Kompilátor automaticky vytvoří úložiště pro události v podobě člena typu delegáta a vytvoří interní `add()`, `remove()`, a `raise()` členské funkce. Datový člen události musí být deklarované uvnitř třídy. Návratový typ návratový typ delegáta musí odpovídat návratový typ obslužné rutiny události.  
  
 *událost bloku*  
 Blok událostí umožňuje explicitně deklarovat a přizpůsobit chování `add()`, `remove()`, a `raise()` metody.  
  
 Můžete použít **operátory +=** a **operator-=** přidávat a odebírat událost obslužné rutiny nebo volání `add()` a `remove()` metody explicitně.  
  
 **událost** je kontextové klíčové slovo; viz [Context-Sensitive Keywords](../windows/context-sensitive-keywords-cpp-component-extensions.md) Další informace.  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [události (C + +/ CX)](http://msdn.microsoft.com/library/windows/apps/hh755799.aspx).  
  
 Pokud chcete přidat a pak odebrat obslužnou rutinu události, je nutné uložit, který je vrácen operace přidání struktury EventRegistrationToken. V operaci odebrání pak musíte použít uložené struktura EventRegistrationToken k identifikaci obslužná rutina události, která se má odebrat.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: `/ZW`  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 **Události** – klíčové slovo umožňuje deklarovat událost. Událost je, že se stane, tak pro třídu poskytují oznámení, když se něco zájmu.  
  
### <a name="syntax"></a>Syntaxe
  
```cpp  
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
  
### <a name="parameters"></a>Parametry
 *Modifikátor*  
 Modifikátor, který lze použít v deklaraci události nebo metodu přistupujícího objektu události.  Možné hodnoty jsou **statické** a **virtuální**.  
  
 *delegate*  
 [Delegovat](../windows/delegate-cpp-component-extensions.md), jehož předpis obslužná rutina události se musí shodovat.  
  
 *EVENT_NAME*  
 Název události  
  
 *return_ value*  
 Na návratový typ metody přistupujícího objektu události.  Chcete-li ověřit, návratový typ musí být **void**.  
  
 *Parametry*  
 (volitelné) Parametry pro `raise` metodu, která odpovídá podpisu *delegovat* parametru.  
  
### <a name="remarks"></a>Poznámky
 Událost je přidružení mezi delegáta a členské funkce (Obslužná rutina události), který reaguje na aktivaci události a umožňuje klientům z jiné třídy, metody, které v souladu s podpisem a návratový typ delegáta základní registrace.  
  
 Delegát může mít jeden nebo více přidružených metody, které se má volat při kódu indikuje, že došlo k události. Událost v jednom programu můžete k dispozici další programy, které jsou cíleny na rozhraní .NET Framework common language runtime.  
  
 Existují dva typy deklarací události:  
  
 *data události*  
 Úložiště pro události v podobě člena typu delegáta, je vytvořen kompilátorem pro datový člen události.  Datový člen události musí být deklarované uvnitř třídy. Se také označuje jako triviální události (viz následující ukázka kódu).  
  
 *bloky události*  
 Událost bloky umožňují přizpůsobit chování přidat, odebrat a vyvolat metody implementací přidat, odebrat a vyvolání metody. Podpis přidat, odebrat a vyvolat metody musí odpovídat signatuře delegáta.  Události bloku nejsou datové členy a jakékoli použití jako datový člen vygeneruje chybu kompilátoru. 
  
 Návratový typ obslužné rutiny události musí odpovídat návratový typ delegáta.  
  
 V rozhraní .NET Framework lze považovat datový člen, jako by šlo metodu samotného (to znamená `Invoke` metoda jeho odpovídající delegáta). Typ delegáta musí předdefinovat deklarace datový člen spravované události. Metoda spravované události naproti tomu implicitně definuje odpovídající spravovaný delegáta, pokud již není definován.  Najdete v ukázce kódu na konci tohoto tématu pro příklad.  
  
 Při deklaraci spravovaného událostí, můžete přidat nebo odebrat přístupové objekty, které se má volat při přidávání nebo odebírání obslužných rutin událostí pomocí operátorů += a-=. Přidat, odebrat a vyvolat metody lze volat explicitně.  
  
 Následující kroky musíte provést k vytvoření a používání událostí v jazyce Visual C++:  
  
1.  Vytvořte nebo Identifikujte delegáta. Pokud definujete vlastní událost, musíte také zajistit, že je delegát, pomocí **události** – klíčové slovo. Pokud předdefinovaná události v rozhraní .NET Framework například pak příjemci události musí pouze znát název delegáta.  
  
2.  Vytvořte třídu, která obsahuje:  
  
    -   Události vytvořené z delegáta.  
  
    -   (volitelné) Metoda, která ověřuje, že instance delegáta deklarovat s **události** – klíčové slovo existuje. V opačném případě tuto logiku musí být umístěn v kódu, který se aktivuje událost.  
  
    -   Metody, které volají události. Tyto metody mohou být přepsání některé funkce základní třídy.  
  
     Tato třída definuje události.  
  
3.  Definujte jednu nebo více tříd, které se připojují k této události metod. Každá z těchto tříd se přidružit k jedné nebo několika metod události v základní třídě.  
  
4.  Použijte události:  
  
    -   Vytvoření objektu třídy, která obsahuje deklaraci události.  
  
    -   Vytvoření objektu třídy obsahující definici události.  
  
 Další informace o jazyce C + +/ CLI událostí, naleznete v tématu  
  
-   [Události v rozhraní](../dotnet/how-to-use-events-in-cpp-cli.md)  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: `/clr`  
  
### <a name="examples"></a>Příklady  

 Následující příklad kódu ukazuje deklarující páry delegáty, události a obslužné rutiny události; přihlášení k odběru (přidávání) obslužné rutiny událostí; volání obslužných rutin událostí; a pak Probíhá rušení odběru (odebrat) obslužné rutiny událostí.  
  
```cpp  
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
  
```Output  
OnClick: 7, 3.14159  
  
OnDblClick: Hello  
```  
  
 Následující příklad kódu ukazuje logikou používanou ke generování `raise` metoda triviální události: Pokud má jeden nebo více odběratelům událost, volání `raise` metoda implicitně nebo explicitně volání delegáta. Pokud je delegát návratový typ není **void** a pokud nejsou k dispozici žádný odběratelů událostí `raise` metoda vrátí výchozí hodnotu pro typ delegáta. Pokud neexistují žádné události odběratele, volání `raise` jednoduše vrací metoda a je vyvolána žádná výjimka. Pokud delegát návratový typ není **void**, je vrácen typ delegáta.  
  
```cpp  
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
  
```Output  
0  
  
688  
```  
  
## <a name="see-also"></a>Viz také  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)