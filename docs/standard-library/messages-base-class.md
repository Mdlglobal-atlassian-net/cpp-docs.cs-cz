---
title: messages_base – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmes/std::messages_base
dev_langs:
- C++
helpviewer_keywords:
- messages_base class
ms.assetid: 9aad38c6-4c13-445d-b096-364bd0836efb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ddde025fa633ccc1b9561acf595de186548ba3a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="messagesbase-class"></a>messages_base – třída

Popisuje základní třídy `int` typ pro katalog zprávy.

## <a name="syntax"></a>Syntaxe

```cpp
struct messages_base : locale::facet {
    typedef int catalog;
    explicit messages_base(size_t _Refs = 0)
};
```

## <a name="remarks"></a>Poznámky

Typ katalogu je synonymum pro typ `int` , který popisuje možné vrácené hodnoty ze zprávy:: [do_open –](../standard-library/messages-class.md#do_open).

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
