---
title: Chyba kompilátoru C2030 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2030
dev_langs:
- C++
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ceccc1088e32382167e7e6400360b30de07fde1d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2030"></a>Chyba kompilátoru C2030
destruktor s chráněné privátním usnadnění nesmí být členem třídy deklarován 'zapečetěné.  
  
 Prostředí Windows Runtime třídy deklarován jako `sealed` nemůže mít chráněný privátní destruktor. Veřejné virtuální a privátní nevirtuálních destruktory jsou povoleny pouze v zapečetěných typech. Další informace najdete v tématu [Ref třídy a struktury](../../cppcx/ref-classes-and-structs-c-cx.md).  
  
 Chcete-li tuto chybu opravit, změňte usnadnění destruktoru.