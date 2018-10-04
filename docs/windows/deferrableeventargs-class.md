---
title: Deferrableeventargs – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::DeferrableEventArgs
- event/Microsoft::WRL::DeferrableEventArgs::GetDeferral
- event/Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::DeferrableEventArgs class
- Microsoft::WRL::DeferrableEventArgs::GetDeferral method
- Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished method
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 20cb959727cb2c515bd82d5b4d5d8e45019c6875
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788484"
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

Byste měli volat tuto metodu po volání zdroje události [invokeall –](../windows/eventsource-invokeall-method.md). Voláním této metody zabrání se dalšímu odložení změněny a vynutí obslužné rutiny dokončení spustit, když se nevytvořily žádné odložení.
