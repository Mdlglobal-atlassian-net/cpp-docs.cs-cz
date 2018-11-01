---
title: auto_gcroot – třída
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot
- msclr.auto_gcroot
- auto_gcroot
helpviewer_keywords:
- auto_gcroot
ms.assetid: b5790912-265d-463e-a486-47302e91042a
ms.openlocfilehash: cb89035d928b251c9cc0427612ce6853a96456a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534235"
---
# <a name="autogcroot-class"></a>auto_gcroot – třída

Správa automatického prostředků (jako [auto_ptr – třída](../standard-library/auto-ptr-class.md)) který slouží k vložení virtuální popisovač do nativního typu.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename _element_type>
class auto_gcroot;
```

#### <a name="parameters"></a>Parametry

*_element_type*<br/>
Spravovaný typ má být vložen.

## <a name="requirements"></a>Požadavky

**Soubor hlaviček** \<msclr\auto_gcroot.h >

**Namespace** msclr –

## <a name="see-also"></a>Viz také

[auto_gcroot](../dotnet/auto-gcroot.md)<br/>
[auto_gcroot Members](../dotnet/auto-gcroot-members.md)<br/>
[Postupy: Deklarace obslužných rutin v nativních typech](../dotnet/how-to-declare-handles-in-native-types.md)<br/>
[auto_handle – třída](../dotnet/auto-handle-class.md)