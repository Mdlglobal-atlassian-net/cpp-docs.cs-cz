---
title: 'Postupy: migrace na - clr: bezpečné (C + +/ CLI) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- migration [C++], verifiable assemblies
- upgrading Visual C++ applications, verifiable assemblies
- verifiable assemblies [C++], migrating to
- /clr compiler option [C++], migrating to /clr:safe
ms.assetid: 75f9aae9-1dcc-448a-aa11-2d96f972f9d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7b12efce8d3566c4fa8824c70e0a6c7ae9d486dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-migrate-to-clrsafe-ccli"></a>Postupy: Přechod na /clr:safe (C++/CLI)
Visual C++ může generovat ověřitelné komponenty pomocí **/CLR: safe**, což způsobí, že kompilátor generuje chyby pro každou konstrukci-ověřitelný kód.  
  
## <a name="remarks"></a>Poznámky  
 Následující problémy se generují ověřitelnosti chyby:  
  
-   Nativní typy. I když se nepoužívá, deklaraci nativní třídy, struktury, ukazatele nebo pole zabrání kompilace.  
  
-   Globální proměnné  
  
-   Volání funkcí do jakékoli nespravované knihovny, včetně common language runtime funkce volání  
  
-   Ověřitelná funkce nemůže obsahovat [static_cast – operátor](../cpp/static-cast-operator.md) pro přetypování dolů. [Static_cast – operátor](../cpp/static-cast-operator.md) lze použít pro přetypování mezi primitivní typy, ale pro přetypování dolů [safe_cast](../windows/safe-cast-cpp-component-extensions.md) nebo přetypování ve stylu jazyka C (která je implementovaná jako [safe_cast](../windows/safe-cast-cpp-component-extensions.md)) je nutné použít.  
  
-   Ověřitelná funkce nemůže obsahovat [reinterpret_cast – operátor](../cpp/reinterpret-cast-operator.md) (nebo ekvivalent žádné přetypování ve stylu jazyka C).  
  
-   Ověřitelná funkce nelze provést na aritmetické [interior_ptr (C + +/ CLI)](../windows/interior-ptr-cpp-cli.md). Může pouze jí přiřadit a přistoupit přes ukazatel.  
  
-   Ověřitelná funkce můžete pouze throw nebo catch ukazatele na odkazové typy, typy hodnot musí být před vyvoláním zabaleny.  
  
-   Ověřitelná funkce lze volat pouze ověřitelné funkce (tak, aby volání modulu CLR nejsou povoleny, zahrnují `AtEntry` / `AtExit`, a proto jsou zakázány globální konstruktory).  
  
-   Nelze použít třídu ověřitelný <xref:System.Runtime.InteropServices.LayoutKind>.  
  
-   Pokud vytváříte EXE, hlavní funkce nelze deklarovat žádné parametry, takže <xref:System.Environment.GetCommandLineArgs%2A> musí použít k načtení argumenty příkazového řádku.  
  
-   Provedení nevirtuálních volání virtuální funkce. Příklad:  
  
    ```  
    // not_verifiable.cpp  
    // compile with: /clr  
    ref struct A {  
       virtual void Test() {}  
    };  
  
    ref struct B : A {};  
  
    int main() {  
       B^ b1 = gcnew B;  
       b1->A::Test();   // Non-virtual call to virtual function  
    }  
    ```  
  
 Navíc následující klíčová slova nelze použít v ověřitelný kód:  
  
-   [nespravované](../preprocessor/managed-unmanaged.md) a [pack](../preprocessor/pack.md) direktivách pragma  
  
-   [holé](../cpp/naked-cpp.md) a [zarovnat](../cpp/align-cpp.md) [__declspec](../cpp/declspec.md) modifikátory  
  
-   [__asm](../assembler/inline/asm.md)  
  
-   [__based](../cpp/based-grammar.md)  
  
-   [__try](../cpp/try-except-statement.md) a `__except`  
  
## <a name="see-also"></a>Viz také  
 [Čistý a ověřitelný kód (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)