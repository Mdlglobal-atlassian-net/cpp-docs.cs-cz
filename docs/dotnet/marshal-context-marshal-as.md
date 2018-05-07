---
title: marshal_context::marshal_as | Microsoft Docs
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
ms.openlocfilehash: 27f27b164d7a00e05e8d080a692f97b696776cbe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="marshalcontextmarshalas"></a>marshal_context::marshal_as
Provede zařazování na konkrétní datový objekt k převedení mezi spravované a nativní datový typ.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
To_Type marshal_as<To_Type>(  
   From_Type input   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v] `input`  
 Hodnota, kterou chcete zařazování na `To_Type` proměnné.  
  
## <a name="return-value"></a>Návratová hodnota  
 Proměnné typu `To_Type` tedy převedenou hodnotu `input`.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce provede zařazování na konkrétní datový objekt. Tuto funkci můžete používat jenom s převody uvedené v tabulce v [přehled zařazování v jazyku C++](../dotnet/overview-of-marshaling-in-cpp.md).  
  
 Pokud se pokusíte zařazování pár typy dat, které nejsou podporovány, `marshal_as` vygenerují chybu [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) v době kompilace. Přečtěte si zprávy zadaný k této chybě Další informace. `C4996` Pro více než jen zastaralé funkce může být generována chyba. Jsou dvě podmínky, které bude generovat tuto chybu pokusu o zařazení pár typy dat, které nejsou podporovány a pokusu o použití `marshal_as` pro převod, který vyžaduje kontext.  
  
 Knihovny zařazování se skládá z několika hlavičkových souborů. Jakékoli převody vyžaduje pouze jeden soubor, ale můžete zahrnout další soubory, pokud je potřeba pro jiné převody. V tabulce v `Marshaling Overview in C++` Určuje, který zařazování soubor by měl být zahrnutý pro každý převod.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří kontextu pro zařazování z `System::String` k `const char *` typ proměnné. Převedená data nebude po řádek, který odstraní kontextu platný.  
  
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
 [marshal_as](../dotnet/marshal-as.md)   
 [marshal_context Class](../dotnet/marshal-context-class.md)