---
title: "Chyba kompilátoru C2030 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2030
dev_langs:
- C++
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c025fe57d411ae4744a10fe9bc062b336e189e83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2030"></a>Chyba kompilátoru C2030
destruktor s chráněné privátním usnadnění nesmí být členem třídy deklarován 'zapečetěné.  
  
 Prostředí Windows Runtime třídy deklarován jako `sealed` nemůže mít chráněný privátní destruktor. Veřejné virtuální a privátní nevirtuálních destruktory jsou povoleny pouze v zapečetěných typech. Další informace najdete v tématu [Ref třídy a struktury](../../cppcx/ref-classes-and-structs-c-cx.md).  
  
 Chcete-li tuto chybu opravit, změňte usnadnění destruktoru.