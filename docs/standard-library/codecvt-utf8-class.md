---
title: codecvt_utf8 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- codecvt/std::codecvt_utf8
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf8 class
ms.assetid: 2a87478f-e2d4-4b8d-ad9c-00add01d1bb0
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0aeb05c5868c1d97713e81f6f09430f64ded9d8b
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="codecvtutf8"></a>codecvt_utf8

Představuje [národního prostředí](../standard-library/locale-class.md) omezující vlastnosti, který převádí mezi široké znaky kódovaná jako UCS-2 nebo UCS 4 a datového proudu bajtů kódovaná jako UTF-8.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parametry

`Elem` Typ elementu široká charakterová.
`Maxcode` Maximální počet znaků pro omezující vlastnost národního prostředí.
`Mode` Informace o konfiguraci pro omezující vlastnost národního prostředí.

## <a name="remarks"></a>Poznámky

Datový proud bajtů je možné zapsat do binárního souboru nebo textového souboru.

## <a name="requirements"></a>Požadavky

Záhlaví: <codecvt> Namespace: – std
