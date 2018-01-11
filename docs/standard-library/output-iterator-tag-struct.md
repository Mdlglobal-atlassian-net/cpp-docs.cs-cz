---
title: "output_iterator_tag – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xutility/std::output_iterator_tag
dev_langs: C++
helpviewer_keywords:
- output_iterator_tag class
- output_iterator_tag struct
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a45dd68f5788244c7d7f1ea72b22af5f96c1a0d8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="outputiteratortag-struct"></a>output_iterator_tag – struktura
Třídu, která poskytuje návratový typ pro **iterator_category –** funkce, která představuje výstupní iterace.  
  
## <a name="syntax"></a>Syntaxe  
  
{} output_iterator_tag – struktura;  
  
## <a name="remarks"></a>Poznámky  
 Třídy značky kategorie se používají jako zkompilovat značky pro výběr algoritmů. Funkce šablony musí najít nejvíce určitou kategorii její argument iterator tak, aby v době kompilace může použít algoritmus maximální efektivitou. Pro každý iterator typu `Iterator`, `iterator_traits` <  `Iterator` >  **:: iterator_category –** musí být definován jako nejvíce značky kategorii, která popisuje iteraci chování.  
  
 Typ je stejný jako **iterator** \< **Iter**> **:: iterator_category –** při **Iter** popisuje objekt, který může sloužit jako iterator výstup.  
  
 Tato značka není parametry na `value_type` nebo `difference_type` pro iterator, stejně jako u jiných iterator značky, protože výstup iterátory není nainstalován žádný `value_type` nebo `difference_type`.  
  
## <a name="example"></a>Příklad  
 V tématu [iterator_traits –](../standard-library/iterator-traits-struct.md) nebo [random_access_iterator_tag –](../standard-library/random-access-iterator-tag-struct.md) příklad použití **iterator_tag**s.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<iterator >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)



