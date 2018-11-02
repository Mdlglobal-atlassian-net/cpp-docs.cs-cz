---
title: lock – třída
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
helpviewer_keywords:
- lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
ms.openlocfilehash: 8876810b15a7d2736f2c8ab0ca1f4c6011918a5f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547131"
---
# <a name="lock-class"></a>lock – třída

Tato třída automatizuje, přičemž zámek pro synchronizaci přístupu k objektu z více vláken.  Když se získá zámek a při jeho zničení verze zámku.

## <a name="syntax"></a>Syntaxe

```
ref class lock;
```

## <a name="remarks"></a>Poznámky

`lock` je k dispozici pouze pro objekty CLR a jde použít jenom v kódu CLR.

Interně používá třídy zámku <xref:System.Threading.Monitor> k synchronizaci přístupu. V tomto tématu další podrobné informace o synchronizaci.

## <a name="requirements"></a>Požadavky

**Soubor hlaviček** \<msclr\lock.h >

**Namespace** msclr –

## <a name="see-also"></a>Viz také

[lock](../dotnet/lock.md)<br/>
[lock – členy](../dotnet/lock-members.md)