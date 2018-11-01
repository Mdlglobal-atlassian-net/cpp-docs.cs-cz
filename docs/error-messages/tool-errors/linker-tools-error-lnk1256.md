---
title: Chyba linkerů LNK1256
ms.date: 11/04/2016
f1_keywords:
- xml
- LNK1256
helpviewer_keywords:
- LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
ms.openlocfilehash: 9d969d1e5bbae92ed49747f761c1b89d1910d4e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492857"
---
# <a name="linker-tools-error-lnk1256"></a>Chyba linkerů LNK1256

Operace ALINK selhala: důvod

Častým důvodem, proč LNK1256 je nesprávné číslo verze pro sestavení. Hodnota 65535 není povolena pro libovolnou část čísla verze sestavení. Platný rozsah pro sestavení verze je 0 – 65534.

LNK1256 můžete také tehdy, když ALINK nelze najít pojmenované kontejneru klíčů. Odstranění kontejneru klíčů a znovu přidat do CSP silného názvu pomocí [Sn.exe (nástroj Strong Name)](/dotnet/framework/tools/sn-exe-strong-name-tool).

Dalším důvodem pro LNK1256 je Neshoda verzí mezi linkeru a Alink.dll. Příčinou může být poškozená instalace sady Visual Studio. Použití **programy a funkce** v Ovládacích panelech Windows opravte nebo přeinstalujte Visual Studio.

Následující ukázka generuje LNK1256:

```
// LNK1256.cpp
// compile with: /clr /LD
// LNK1256 expected
[assembly:System::Reflection::AssemblyVersionAttribute("1.0.65535")];
public class CMyClass {
public:
   int value;
};
```