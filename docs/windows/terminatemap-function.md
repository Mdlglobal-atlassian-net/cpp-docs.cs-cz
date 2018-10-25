---
title: Terminatemap – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
dev_langs:
- C++
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bc5aec34177572552d119df967c9d25571b6cb63
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066029"
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