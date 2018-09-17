---
title: marshal_context::marshal_as | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context::marshal_as
- marshal_context.marshal_as
- msclr.interop.marshal_context.marshal_as
- msclr::interop::marshal_context::marshal_as
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 24a1afee-51c0-497c-948c-f77fe43635c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f88d086c76ea6b56f1bb049b886df70ceadbdbb9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707899"
---
# <a name="marshalcontextmarshalas"></a>marshal_context::marshal_as
Provádí zařazování na konkrétní datový objekt k převodu mezi spravovaný a nativní datovým typem.  
  
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
 Tato funkce provede zařazování na konkrétní datový objekt. Tuto funkci použít pouze s převody uvedené v tabulce v [Overview of Marshaling in C++](../dotnet/overview-of-marshaling-in-cpp.md).  
  
 Pokud se pokusíte zařazování pár datových typů, které nejsou podporované. zahrnuje `marshal_as` vygeneruje chybu [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) v době kompilace. Přečtěte si zprávy zadané k této chybě Další informace. `C4996` Chyby mohou být generovány pro více než jen zastaralé funkce. Jsou dvě podmínky, které budou generovat tato chyba pokusu o zařazení pár datových typů, které nejsou podporovány a pokusu o použití `marshal_as` pro převod, který vyžaduje kontext.  
  
 Zařazovací knihovna se skládá z několika hlavičkové soubory. Jakýkoli převod vyžaduje pouze jeden soubor, ale pokud je potřeba pro ostatní převody, které můžete zahrnout další soubory. V tabulce v `Marshaling Overview in C++` označuje zařazování soubor, který by měl být zahrnutý pro každý převod.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří kontext pro zařazování z `System::String` k `const char *` typ proměnné. Převedená data nebudou po řádek, který odstraní kontextu platný.  
  
```  
// marshal_context_test.cpp  
// compile with: /clr  
#include <stdlib.h>  
#include <string.h>  
#include <msclr\marshal.h>  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   marshal_context^ context = gcnew marshal_context();  
   String^ message = gcnew String("Test String to Marshal");  
   const char* result;  
   result = context->marshal_as<const char*>( message );  
   delete context;  
   return 0;  
}  
```  
  
## <a name="requirements"></a>Požadavky  
 **Soubor hlaviček:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, nebo \<msclr\marshal_atl.h >  
  
 **Namespace:** msclr::interop  
  
## <a name="see-also"></a>Viz také  
 [Přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as –](../dotnet/marshal-as.md)   
 [marshal_context Class](../dotnet/marshal-context-class.md)