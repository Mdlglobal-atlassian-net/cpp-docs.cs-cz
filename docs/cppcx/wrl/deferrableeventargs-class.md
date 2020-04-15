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
ms.openlocfilehash: bae2472a75ab77f138fcee0951a6b869cc7c8e82
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372569"
---
# <a name="deferrableeventargs-class"></a>DeferrableEventArgs – třída

Třída šablony použitá pro typy argumentů události pro časově rozlišené události.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename TEventArgsInterface, typename TEventArgsClass>
class DeferrableEventArgs : public TEventArgsInterface;
```

### <a name="parameters"></a>Parametry

*Rozhraní TEventArgs*<br/>
Typ rozhraní, který deklaruje argumenty pro odložené události.

*Třída TEventArgsClass*<br/>
Třída, která implementuje *TEventArgsInterface*.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                                         | Popis
------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------
[DeferrableEventArgs::GetDeferral](#getdeferral)             | Získá odkaz na [deferral](/uwp/api/windows.foundation.deferral) objekt, který představuje odložené události.
[DeferrableEventArgs::InvokeAllFinished](#invokeallfinished) | Volána k označení, že veškeré zpracování pro zpracování odložené události je dokončena.

## <a name="remarks"></a>Poznámky

Instance této třídy jsou předány obslužné rutiny událostí pro odložené události. Parametry šablony představují rozhraní, které definuje podrobnosti argumentů události pro určitý typ odložené události a třídu, která implementuje toto rozhraní.

Třída se zobrazí jako první argument obslužné rutiny události pro odloženou událost. Můžete volat [GetDeferral](#getdeferral) metoda získat [deferral](/uwp/api/windows.foundation.deferral) objekt, ze kterého můžete získat všechny informace o odložené události. Po dokončení zpracování událostí, měli byste volat Complete na objekt deferral. Potom byste měli volat [InvokeAllFinished](#invokeallfinished) na konci metody obslužné rutiny události, která zajišťuje, že dokončení všech odložených událostí je správně sděleno.

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Obor názvů:** Microsoft::WRL

## <a name="deferrableeventargsgetdeferral"></a><a name="getdeferral"></a>DeferrableEventArgs::GetDeferral

Získá odkaz na [deferral](/uwp/api/windows.foundation.deferral) objekt, který představuje odložené události.

```cpp
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)
```

### <a name="parameters"></a>Parametry

*Výsledek*<br/>
Ukazatel, který bude odkazovat na objekt [deferral](/uwp/api/windows.foundation.deferral) po dokončení volání.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

## <a name="deferrableeventargsinvokeallfinished"></a><a name="invokeallfinished"></a>DeferrableEventArgs::InvokeAllFinished

Volána k označení, že veškeré zpracování pro zpracování odložené události je dokončena.

```cpp
void InvokeAllFinished()
```

### <a name="remarks"></a>Poznámky

Tuto metodu byste měli volat po volání zdroje události [InvokeAll](eventsource-class.md#invokeall). Volání této metody zabrání další odložení přijata a vynutí dokončení obslužné rutiny provést, pokud byly provedeny žádné odklady.
