---
title: "is_trivially_copy_constructible – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_trivially_copy_constructible
dev_langs: C++
helpviewer_keywords: is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 465d5a1756a416eac2c01c5191b4f63f986ffcba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible – třída
Testy, pokud má typ trivial kopírovacího konstruktoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>
struct is_trivially_copy_constructible;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ, na který chcete odeslat dotaz.  
  
## <a name="remarks"></a>Poznámky  
 Instance predikátem typu obsahuje hodnotu true, pokud typ `T` je třída, která má trivial kopírovacího konstruktoru, jinak má hodnotu false.  
  
 Kopírovací konstruktor pro třídu `T` je jednoduchá, pokud je implicitně deklarovaná, třída `T` nemá žádné virtuální funkce nebo virtuální základů, všechny přímé základů třídy `T` mít trivial kopírovací konstruktory, třídy všechny nestatickou datové členy typu třídy trivial kopie konstruktorů a třídy všechny členy nestatické datové pole typu třídy trivial kopírovací konstruktory.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [< type_traits >](../standard-library/type-traits.md)



