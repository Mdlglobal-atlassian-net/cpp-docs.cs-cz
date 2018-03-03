---
title: "Úložiště adres | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bd82f6f5046cf910fbc871be37d4af5856796792
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="storage-of-addresses"></a>Úložiště adres
Velikost úložiště potřebná pro adresu a její význam závisí na implementaci kompilátoru. Není zaručeno, že ukazatele na různé typy budou mít stejnou délku. Proto **sizeof (char \*)** není nutně roven **sizeof (int \*)**.  
  
 **Konkrétní Microsoft**  
  
 Pro kompilátor Microsoft C **sizeof (char \*)** rovná **sizeof (int \*)**.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Deklarace ukazatelů](../c-language/pointer-declarations.md)