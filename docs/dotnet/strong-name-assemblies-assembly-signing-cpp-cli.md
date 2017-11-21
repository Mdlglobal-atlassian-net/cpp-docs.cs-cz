---
title: "Sestavení se silným názvem (podepisování sestavení) (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- assemblies [C++]
- signing assemblies
- .NET Framework [C++], assembly signing
- assemblies [C++], signing
- linker [C++], assembly signing
- strong-named assemblies [C++]
ms.assetid: c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 32a9502bbb1143e23ee542c1d9fff593925c527a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
  
-   [/ DELAYSIGN (částečně podepsané sestavení)](../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/ KEYFILE (zadat klíč nebo pár klíčů pro podepsání sestavení)](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/ KEYCONTAINER (zadat kontejner klíčů pro podepsání sestavení)](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
 Další informace o silných sestaveních najdete v tématu [vytvoření a použití sestavení](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).  
  
## <a name="see-also"></a>Viz také  
 [.NET – programování s C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)