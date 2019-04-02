---
title: TerminateMap – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: 17d02ea9cade0301798a5d6625f8eb9a568cb2cc
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786581"
---
# <a name="terminatemap-function"></a>TerminateMap – funkce

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
inline bool TerminateMap(
   _In_ ModuleBase *module,
   _In_opt_z_ const wchar_t *serverName,
    bool forceTerminate) throw()
```

### <a name="parameters"></a>Parametry

*module*<br/>
A [modulu](module-class.md).

*serverName*<br/>
Název dílčí sady objekty pro vytváření tříd v modulu určené parametrem *modulu*.

*forceTerminate*<br/>
**Hodnota TRUE** ukončení třídy jsou aktivní, bez ohledu na to, že objekty pro vytváření **false** není ukončit objekty pro vytváření tříd, pokud je aktivní libovolný objekt pro vytváření.

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** všechny objekty pro vytváření tříd byl ukončen; v opačném případě **false**.

## <a name="remarks"></a>Poznámky

Třída továrny v zadaném modulu vypne.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)