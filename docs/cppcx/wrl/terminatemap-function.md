---
title: TerminateMap – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: 560f563e43fc8b818b04cd0bda6b01fbc916cb84
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213548"
---
# <a name="terminatemap-function"></a>TerminateMap – funkce

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
inline bool TerminateMap(
   _In_ ModuleBase *module,
   _In_opt_z_ const wchar_t *serverName,
    bool forceTerminate) throw()
```

### <a name="parameters"></a>Parametry

*module*<br/>
[Modul](module-class.md).

*serverName*<br/>
Název podmnožiny tříd Factory v modulu určeném parametrem *Module*.

*forceTerminate*<br/>
**true** pro ukončení třídy Factory bez ohledu na to, že jsou aktivní; **false** – Pokud je aktivní nějaký objekt factory, neukončí se továrny tříd.

## <a name="return-value"></a>Návratová hodnota

**true** , pokud byly ukončeny všechny továrny tříd; v opačném případě **false**.

## <a name="remarks"></a>Poznámky

Vypne továrny tříd v zadaném modulu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** modul. h

**Obor názvů:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)
