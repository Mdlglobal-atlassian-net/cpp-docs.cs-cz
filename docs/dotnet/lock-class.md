---
title: Lock – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::lock
- msclr.lock
- lock
dev_langs:
- C++
helpviewer_keywords:
- lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7ef0887ca3eec7510717aab21ba4c6c7aba98d25
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380292"
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