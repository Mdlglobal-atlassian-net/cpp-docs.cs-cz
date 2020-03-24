---
title: událost (C++/CLI a C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- event
- event_cpp
helpviewer_keywords:
- event keyword [C++]
ms.assetid: c4998e42-883c-4419-bbf4-36cdc979dd27
ms.openlocfilehash: 90682ba699f6316cb6b38a3b78c44e853cd5473f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172383"
---
# <a name="event--ccli-and-ccx"></a>událost (C++/CLI a C++/CX)

Klíčové slovo **Event** deklaruje *událost*, což je oznámení registrovaným předplatitelům (*obslužné rutiny událostí*), ke kterým došlo v nějakém zájmu.

## <a name="all-runtimes"></a>Všechny moduly runtime

C++/CX podporuje deklaraci *členu události* nebo *bloku událostí*. Člen události je zkrácený pro deklaraci bloku události. Ve výchozím nastavení deklaruje člen události `add()`, `remove()`a `raise()` funkce, které jsou deklarovány explicitně v bloku událostí. Chcete-li přizpůsobit funkce v členu události, deklarujte blok události místo toho a potom popište požadované funkce.

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

*upravující*<br/>
Modifikátor, který lze použít buď pro deklaraci události, nebo pro metodu přístupového objektu události.  Možné hodnoty jsou **statické** a **virtuální**.

*delegate*<br/>
[Delegát](delegate-cpp-component-extensions.md), jehož signatura musí být v obslužné rutině události shodná.

*event_name*<br/>
Název události.

*return_value*<br/>
Návratová hodnota metody přístupového objektu události  Aby bylo možné typ vrácené hodnoty ověřit, musí být návratový typ **void**.

*parameters*<br/>
volitelné Parametry pro metodu `raise`, která se shoduje s signaturou parametru *delegáta* .

### <a name="remarks"></a>Poznámky

Událost je přidružení mezi delegátem a členskou funkcí (obslužným rutinou události), která reaguje na aktivaci události a umožňuje klientům z libovolné třídy registrovat metody, které odpovídají signatuře a návratový typ nadřazeného delegáta.

Existují dva druhy deklarací událostí:

*datový člen události*<br/>
Kompilátor automaticky vytvoří úložiště pro událost ve formě člena typu delegáta a vytvoří interní `add()`, `remove()`a `raise()` členské funkce. Datový člen události musí být deklarovaný uvnitř třídy. Návratový typ návratového typu delegáta musí odpovídat návratový typ obslužné rutiny události.

*blok událostí*<br/>
Blok událostí umožňuje explicitně deklarovat a přizpůsobit chování metod `add()`, `remove()`a `raise()`.

**Operátory + =** a **-=** můžete použít k přidání a odebrání obslužné rutiny události nebo volání metod `add()` a `remove()` explicitně.

**událost** je kontextově závislé klíčové slovo; Další informace najdete v tématu [Kontextově závislá klíčová slova](context-sensitive-keywords-cpp-component-extensions.md) .

## <a name="windows-runtime"></a>prostředí Windows Runtime

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [události (C++/CX)](../cppcx/events-c-cx.md).

Pokud máte v úmyslu přidat a poté odebrat obslužnou rutinu události, je nutné uložit strukturu EventRegistrationToken, která je vrácena operací Add. Pak je nutné v operaci odebrat použít uloženou strukturu EventRegistrationToken k identifikaci obslužné rutiny události, která má být odebrána.

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Klíčové slovo **události** umožňuje deklarovat událost. Událost je způsob, jakým může Třída poskytnout oznámení v případě, že dojde k nějakému zájmu.

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

*upravující*<br/>
Modifikátor, který lze použít buď pro deklaraci události, nebo pro metodu přístupového objektu události.  Možné hodnoty jsou **statické** a **virtuální**.

*delegate*<br/>
[Delegát](delegate-cpp-component-extensions.md), jehož signatura musí být v obslužné rutině události shodná.

*event_name*<br/>
Název události.

*return_value*<br/>
Návratová hodnota metody přístupového objektu události  Aby bylo možné typ vrácené hodnoty ověřit, musí být návratový typ **void**.

*parameters*<br/>
volitelné Parametry pro metodu `raise`, která se shoduje s signaturou parametru *delegáta* .

### <a name="remarks"></a>Poznámky

Událost je přidružení mezi delegátem a členskou funkcí (obslužným rutinou události), která reaguje na aktivaci události a umožňuje klientům z libovolné třídy registrovat metody, které odpovídají signatuře a návratový typ nadřazeného delegáta.

Delegát může mít jednu nebo více přidružených metod, které budou volány, když váš kód indikuje, že došlo k události. Událost v jednom programu může být zpřístupněna ostatním programům, které cílí na .NET Framework modul CLR (Common Language Runtime).

Existují dva druhy deklarací událostí:

*datové členy události*<br/>
Úložiště pro událost ve formě člena typu delegáta je vytvořeno kompilátorem pro události datových členů.  Datový člen události musí být deklarovaný uvnitř třídy. Toto je také známo jako triviální událost (viz Ukázka kódu níže).

*bloky událostí*<br/>
Bloky událostí umožňují přizpůsobit chování metod přidat, odebrat a vyvolat implementací metod přidání, odebrání a vyvolání. Signatura metod Add, Remove a vyvolávají se musí shodovat s signaturou delegáta.  Události bloku událostí nejsou datové členy a při jakémkoli použití jako datový člen se vygeneruje chyba kompilátoru.

Návratový typ obslužné rutiny události musí odpovídat návratový typ delegátu.

V .NET Framework můžete s datovým členem zacházet, jako by šlo o metodu (to znamená `Invoke` metoda příslušného delegáta). Musíte předdefinovat typ delegáta pro deklaraci spravovaného datového člena události. Naproti tomu spravovaná metoda události implicitně definuje odpovídající spravovaný delegát, pokud ještě není definovaný.  Příklad najdete v ukázce kódu na konci tohoto tématu.

Při deklaraci spravované události můžete zadat přidat a odebrat přistupující objekty, které budou volány při přidání nebo odebrání obslužných rutin událostí pomocí operátorů + = a-=. Metody přidat, odebrat a vyvolat lze explicitně volat.

Aby bylo možné vytvářet a používat události v jazyce Visual C++, je nutné provést následující kroky:

1. Vytvořte nebo Identifikujte delegáta. Pokud definujete vlastní událost, musíte také zajistit, aby byl delegát pro použití s klíčovým slovem **události** . Pokud je tato událost předdefinovaná, v .NET Framework například, že spotřebitelé události potřebují znát pouze název delegáta.

2. Vytvořte třídu, která obsahuje:

   - Událost vytvořená z delegáta.

   - Volitelné Metoda, která ověřuje, zda existuje instance delegáta deklarované s klíčovým slovem **události** . V opačném případě musí být tato logika umístěna v kódu, který událost aktivuje.

   - Metody, které volají událost. Tyto metody mohou být popsány u některých funkcí základní třídy.

   Tato třída definuje událost.

3. Definujte jednu nebo více tříd, které spojují metody události. Každá z těchto tříd bude přidružit jednu nebo více metod k události v základní třídě.

4. Použijte událost:

   - Vytvořte objekt třídy, která obsahuje deklaraci události.

   - Vytvořte objekt třídy, která obsahuje definici události.

Další informace o událostech C++/CLI najdete v tématu.

- [Události v rozhraní](../dotnet/how-to-use-events-in-cpp-cli.md)

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad kódu ukazuje deklaraci párů delegátů, událostí a obslužných rutin událostí; odběr (přidávání) obslužných rutin událostí; vyvolání obslužných rutin událostí; a potom odhlášení odběru (odebrání) obslužných rutin událostí.

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

Následující příklad kódu ukazuje logiku použitou k vygenerování `raise` metody triviální události: Pokud má událost jednoho nebo více odběratelů, volání metody `raise` implicitně nebo explicitně volá delegáta. Pokud návratový typ delegáta není **void** a pokud jsou k dispozici odběratelé s nulovými událostmi, metoda `raise` vrátí výchozí hodnotu pro typ delegáta. Pokud neexistují předplatitelé události, volání metody `raise` jednoduše vrátí a není vyvolána žádná výjimka. Pokud typ vrácené hodnoty delegáta není **void**, je vrácen typ delegáta.

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

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)
