---
title: AgileEventSource – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
helpviewer_keywords:
- AgileEventSource class
ms.openlocfilehash: 71a70f783d8f8967d755bb788f4aae4861340d64
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214185"
---
# <a name="agileeventsource-class"></a>AgileEventSource – třída

Představuje událost, která je vyvolána agilní komponentou, což je komponenta, ke které lze přistupovat z libovolného vlákna. Dědí z objektu [EventSource](eventsource-class.md) a Přepisuje `Add` členskou funkci s dalším parametrem typu pro zadání možností pro vyvolání agilní události.

## <a name="syntax"></a>Syntaxe

```cpp
template<
    typename TDelegateInterface,
    typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>
>
class AgileEventSource :
    public Microsoft::WRL::EventSource<
        TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>Parametry

*TDelegateInterface*<br/>
Rozhraní k delegátovi, který představuje obslužnou rutinu události.

*TEventSourceOptions*<br/>
Struktura [InvokeModeOptions](invokemodeoptions-structure.md) , jejíž pole invokeMode je nastaveno na `InvokeMode::StopOnFirstError` nebo `InvokeMode::FireAll`.

## <a name="remarks"></a>Poznámky

Velká většina komponent v prostředí Windows Runtime je agilní komponenty. Další informace najdete v tématu [dělení na vlákna a zařazováníC++(/CX)](../../cppcx/threading-and-marshaling-c-cx.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`EventSource`

`AgileEventSource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Event. h

**Obor názvů:** Microsoft:: WRL

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[AgileEventSource:: Add – metoda](#add)|Připojí událost agilní události reprezentované zadaným rozhraním delegáta k sadě obslužných rutin událostí pro aktuální objekt **AgileEventSource** .|

## <a name="agileeventsourceadd-method"></a><a name="add"></a>AgileEventSource:: Add – metoda

Připojí obslužnou rutinu události reprezentované zadaným rozhraním delegáta k sadě obslužných rutin událostí pro aktuální objekt [EventSource](eventsource-class.md) .

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Parametry

*delegateInterface*<br/>
Rozhraní objektu delegáta, který představuje obslužnou rutinu události.

*klíčové*<br/>
Po dokončení této operace bude popisovač reprezentující událost. Tento token použijte jako parametr pro metodu `Remove()` pro zahození obslužné rutiny události.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě hodnota HRESULT, která označuje chybu.

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)
