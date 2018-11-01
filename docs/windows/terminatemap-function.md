---
title: TerminateMap – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: efee7edfc1085288b3220698024cb0deeb4e71af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643219"
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
A [modulu](../windows/module-class.md).

*název_serveru*<br/>
Název dílčí sady objekty pro vytváření tříd v modulu určené parametrem *modulu*.

*forceTerminate*<br/>
**Hodnota TRUE** ukončení třídy jsou aktivní, bez ohledu na to, že objekty pro vytváření **false** není ukončit objekty pro vytváření tříd, pokud je aktivní libovolný objekt pro vytváření.

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** všechny objekty pro vytváření tříd byl ukončen; v opačném případě **false**.

## <a name="remarks"></a>Poznámky

Třída továrny v zadaném modulu vypne.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)