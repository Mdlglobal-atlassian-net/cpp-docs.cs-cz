---
title: marshal_context – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6bf712e960cbf96ccef6c3a3e4efebdad9045818
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33136991"
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