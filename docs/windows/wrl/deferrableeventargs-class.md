---
title: DeferrableEventArgs – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::DeferrableEventArgs
- event/Microsoft::WRL::DeferrableEventArgs::GetDeferral
- event/Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished
helpviewer_keywords:
- Microsoft::WRL::DeferrableEventArgs class
- Microsoft::WRL::DeferrableEventArgs::GetDeferral method
- Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished method
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
ms.openlocfilehash: 509686556bd06a6ec9d059593be46d0fc6a3876d
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334737"
---
# <a name="deferrableeventargs-class"></a>DeferrableEventArgs – třída

Třída šablony použité pro typy argumentů událostí pro odložení.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename TEventArgsInterface, typename TEventArgsClass>
class DeferrableEventArgs : public TEventArgsInterface;
```

### <a name="parameters"></a>Parametry

*TEventArgsInterface*<br/>
Typ rozhraní, který deklaruje argumenty pro odložené událost.

*TEventArgsClass*<br/>
Třída, která implementuje *TEventArgsInterface*.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

Název                                                         | Popis
------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------
[Deferrableeventargs::getdeferral –](#getdeferral)             | Získá odkaz na [odložení](http://go.microsoft.com/fwlink/p/?linkid=526520) objekt, který představuje odložené událost.
[Deferrableeventargs::invokeallfinished –](#invokeallfinished) | Volá se, že je veškeré zpracování zpracování odložené události dokončení.

## <a name="remarks"></a>Poznámky

Instance této třídy jsou předány do obslužné rutiny událostí pro odložené události. Parametry šablony představují rozhraní, které definuje podrobnosti argumenty událostí pro konkrétní typ odloženého události a třídu, která implementuje rozhraní.

Třída se zobrazí jako první argument pro obslužnou rutinu události pro odložené událost. Můžete volat [GetDeferral](#getdeferral) metodu k získání [odložení](http://go.microsoft.com/fwlink/p/?linkid=526520) objektu, ze kterého můžete získat všechny informace o odložených události. Po dokončení zpracování událostí, měli byste zavolat Complete odložení objektu. Potom byste měli volat [InvokeAllFinished](#invokeallfinished) na konci metody obslužné rutiny události, které zajišťuje, že je správně adrese dokončení všech odložené události.

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL

## <a name="getdeferral"></a>Deferrableeventargs::getdeferral –

Získá odkaz na [odložení](http://go.microsoft.com/fwlink/p/?linkid=526520) objekt, který představuje odložené událost.

```cpp
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)
```

### <a name="parameters"></a>Parametry

*výsledek*<br/>
Ukazatel, který bude odkazovat [odložení](http://go.microsoft.com/fwlink/p/?linkid=526520) objektu po dokončení volání.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="invokeallfinished"></a>Deferrableeventargs::invokeallfinished –

Volá se, že je veškeré zpracování zpracování odložené události dokončení.

```cpp
void InvokeAllFinished()
```

### <a name="remarks"></a>Poznámky

Byste měli volat tuto metodu po volání zdroje události [invokeall –](eventsource-class.md#invokeall). Voláním této metody zabrání se dalšímu odložení změněny a vynutí obslužné rutiny dokončení spustit, když se nevytvořily žádné odložení.