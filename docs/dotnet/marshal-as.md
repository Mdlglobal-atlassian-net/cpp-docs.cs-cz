---
title: marshal_as | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
dev_langs:
- C++
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2f57db502be6e34d275e3aba0e7705992b3c4d0d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701620"
---
# <a name="marshalas"></a>marshal_as
Tato metoda převádí data mezi nativními a spravovanými prostředími.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
To_Type marshal_as<To_Type>(  
   From_Type input   
);  
```  
  
#### <a name="parameters"></a>Parametry  
*Vstup*<br/>
[in] Hodnota, kterou chcete zařadit na `To_Type` proměnné.  
  
## <a name="return-value"></a>Návratová hodnota  
 Proměnné typu `To_Type` , který je převedená hodnota `input`.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je jednodušší způsob, jak převést dat mezi nativními a spravovanými typy. Pokud chcete zjistit, jaké typy dat jsou podporovány, naleznete v tématu [Overview of Marshaling in C++](../dotnet/overview-of-marshaling-in-cpp.md). Některé převodů dat vyžadují kontextu. Tyto typy dat můžete převádět pomocí [marshal_context Class](../dotnet/marshal-context-class.md).  
  
 Pokud se pokusíte zařazování pár datových typů, které nejsou podporované. zahrnuje `marshal_as` vygeneruje chybu [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) v době kompilace. Přečtěte si zprávy zadané k této chybě Další informace. `C4996` Chyby mohou být generovány pro více než jen zastaralé funkce. Jedním z příkladů je pokusu o zařazení pár datových typů, které nejsou podporovány.  
  
 Zařazovací knihovna se skládá z několika hlavičkové soubory. Jakýkoli převod vyžaduje pouze jeden soubor, ale pokud je potřeba pro ostatní převody, které můžete zahrnout další soubory. Pokud chcete zjistit, které převody jsou přidruženy soubory, které, podívejte se v tabulce v `Marshaling Overview`. Bez ohledu na to co převodu chcete udělat, požadavek na obor názvů je vždy v platnosti.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu zařazuje z `const char*` k `System::String` typ proměnné.  
  
```  
// marshal_as_test.cpp  
// compile with: /clr  
#include <stdlib.h>  
#include <string.h>  
#include <msclr\marshal.h>  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   const char* message = "Test String to Marshal";  
   String^ result;  
   result = marshal_as<String^>( message );  
   return 0;  
}  
```  
  
## <a name="requirements"></a>Požadavky  
 **Soubor hlaviček:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, nebo \<msclr\marshal_atl.h >  
  
 **Namespace:** msclr::interop  
  
## <a name="see-also"></a>Viz také  
 [Přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_context Class](../dotnet/marshal-context-class.md)