---
title: auto_gcroot – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot
- msclr.auto_gcroot
- auto_gcroot
dev_langs:
- C++
helpviewer_keywords:
- auto_gcroot
ms.assetid: b5790912-265d-463e-a486-47302e91042a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 48412a932ff3752b0613f7045cd88992332b7917
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423222"
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