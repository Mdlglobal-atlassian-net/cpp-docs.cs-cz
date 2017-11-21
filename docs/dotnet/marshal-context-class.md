---
title: "marshal_context – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: marshal_context
dev_langs: C++
helpviewer_keywords: marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 55039f216f2c2b7f3ba04bebaf086dd66c13c779
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="marshalcontext-class"></a>marshal_context – třída
Tato třída převádí data mezi nativní a spravovaná prostředí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class marshal_context  
```  
  
## <a name="remarks"></a>Poznámky  
 Použití `marshal_context` třídu pro převody dat, které vyžadují kontextu. V tématu [přehled zařazování v jazyku C++](../dotnet/overview-of-marshaling-in-cpp.md) Další informace o které převody vyžadují kontextu a který zařazování soubor musí být zahrnuty. Výsledek zařazování při použití kontextu je platný pouze dokud `marshal_context` objekt zničena. Pokud chcete zachovat sady výsledků, musíte zkopírovat data.  
  
 Stejné `marshal_context` lze použít pro více převody data. Opětovné použití kontext tímto způsobem nebude mít vliv na výsledky z předchozích zařazování volání.  
  
## <a name="requirements"></a>Požadavky  
 **Soubor hlaviček:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, nebo \<msclr\marshal_atl.h >  
  
 **Namespace:** msclr::interop  
  
## <a name="see-also"></a>Viz také  
 [Přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as](../dotnet/marshal-as.md)