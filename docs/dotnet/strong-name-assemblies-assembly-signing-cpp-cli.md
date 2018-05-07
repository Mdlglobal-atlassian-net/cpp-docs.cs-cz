---
title: Sestavení se silným názvem (podepisování sestavení) (C + +/ CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assemblies [C++]
- signing assemblies
- .NET Framework [C++], assembly signing
- assemblies [C++], signing
- linker [C++], assembly signing
- strong-named assemblies [C++]
ms.assetid: c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5d7ae911d2572a35ee8dbb21d5484b4679b64c4d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="strong-name-assemblies-assembly-signing-ccli"></a>Sestavení se silným názvem (Podepisování sestavení) (C++/CLI)
Toto téma popisuje, jak se můžete přihlásit sestavení, často označuje jako poskytnutí vašeho sestavení silným názvem.  
  
## <a name="remarks"></a>Poznámky  
 Pokud používáte Visual C++, použijte možnosti linkeru podepsat své sestavení, aby se zabránilo problémy související s atributy CLR pro podepsání sestavení:  
  
-   <xref:System.Reflection.AssemblyDelaySignAttribute>  
  
-   <xref:System.Reflection.AssemblyKeyFileAttribute>  
  
-   <xref:System.Reflection.AssemblyKeyNameAttribute>  
  
 Důvody není pomocí atributů zahrnují skutečnost, že je název klíče viditelné v sestavení metadat, které může představovat bezpečnostní riziko, pokud název souboru obsahuje důvěrné informace. Proces sestavení používá vývojového prostředí jazyka Visual C++ také zruší platnost klíč, pomocí kterého je podepsaná sestavení, pokud používáte atributy CLR umožnit sestavení silným názvem a poté spusťte nástroj následného zpracování jako mt.exe na sestavení.  
  
 Pokud sestavení na příkazovém řádku, použijte možnosti linkeru podepsat své sestavení a spusťte nástroj následného zpracování (např. mt.exe), musíte znovu podepsat sestavení s sn.exe. Alternativně můžete sestavit a zpoždění podepsání sestavení a po spuštění nástroje pro následné zpracování, dokončení podepisování.  
  
 Pokud používáte podepisování atributů při sestavování ve vývojovém prostředí, můžete úspěšně podepsat sestavení explicitně voláním sn.exe ([Sn.exe (nástroj silným názvem)](/dotnet/framework/tools/sn-exe-strong-name-tool)) v události po sestavení. Další informace najdete v tématu [určení událostí sestavení](../ide/specifying-build-events.md). Časy sestavení může být nižší, pokud používáte atributy a události po sestavení, ve srovnání s použitím možnosti linkeru.  
  
 Následující možnosti linkeru podporují podepsání sestavení:  
  
-   [/DELAYSIGN (částečné podepsání sestavení)](../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/KEYFILE (zadání klíče nebo páru klíčů pro podpis sestavení)](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/KEYCONTAINER (zadání kontejneru klíčů pro podpis sestavení)](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
 Další informace o silných sestaveních najdete v tématu [vytvoření a použití sestavení](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).  
  
## <a name="see-also"></a>Viz také  
 [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)