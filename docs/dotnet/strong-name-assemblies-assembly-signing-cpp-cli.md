---
title: Sestavení se silným názvem (Podepisování sestavení) (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- assemblies [C++]
- signing assemblies
- .NET Framework [C++], assembly signing
- assemblies [C++], signing
- linker [C++], assembly signing
- strong-named assemblies [C++]
ms.assetid: c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc
ms.openlocfilehash: c23c3b70a2152fbceb771e085b73d7daf7aa3c2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527553"
---
# <a name="strong-name-assemblies-assembly-signing-ccli"></a>Sestavení se silným názvem (Podepisování sestavení) (C++/CLI)

Toto téma popisuje, jak můžete podepsat sestavení, označovaný také jako poskytnutí silného názvu vašeho sestavení.

## <a name="remarks"></a>Poznámky

Při použití jazyka Visual C++, podepsat vaše sestavení, aby se zabránilo problémům, které souvisí s atributy CLR pro podepsání sestavení pomocí možnosti linkeru:

- <xref:System.Reflection.AssemblyDelaySignAttribute>

- <xref:System.Reflection.AssemblyKeyFileAttribute>

- <xref:System.Reflection.AssemblyKeyNameAttribute>

Mezi důvody bez použití atributů patří skutečnost, že název klíče, který je viditelný v sestavení metadat, což může představovat bezpečnostní riziko, pokud název souboru obsahuje důvěrné informace. Proces sestavení ve vývojovém prostředí Visual C++ navíc skončí platnost všech klíč, pomocí kterého je sestavení podepsáno, je-li poskytnout sestavení silným názvem pomocí atributů CLR a pak spusťte následného zpracování nástroje, jako je mt.exe sestavení.

Pokud podepsat sestavení pomocí možnosti propojovacího programu sestavení na příkazovém řádku a pak spusťte nástroj následného zpracování (například mt.exe), musíte znovu podepsat sestavení s sn.exe. Alternativně můžete vytvářet a zpoždění podepsání sestavení a po spuštění nástroje následného zpracování, dokončení podpisu.

Pokud používáte podepisování atributů při sestavování ve vývojovém prostředí, můžete podepsat sestavení úspěšně explicitně voláním sn.exe ([Sn.exe (nástroj Strong Name)](/dotnet/framework/tools/sn-exe-strong-name-tool)) v události po sestavení. Další informace najdete v tématu [určení událostí sestavení](../ide/specifying-build-events.md). Dobu sestavení může být nižší, pokud používáte atributy a událost po sestavení, ve srovnání s použitím možnosti linkeru.

Následující možnosti linkeru podporují podepisování sestavení:

- [/DELAYSIGN (částečné podepsání sestavení)](../build/reference/delaysign-partially-sign-an-assembly.md)

- [/KEYFILE (zadání klíče nebo páru klíčů pro podpis sestavení)](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER (zadání kontejneru klíčů pro podpis sestavení)](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

Další informace o silné sestavení naleznete v tématu [vytvoření a použití sestavení](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).

## <a name="see-also"></a>Viz také

[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)