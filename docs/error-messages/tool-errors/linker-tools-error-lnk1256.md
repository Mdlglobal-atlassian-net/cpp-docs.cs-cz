---
title: Chyba linkerů LNK1256
ms.date: 11/04/2016
f1_keywords:
- LNK1256
helpviewer_keywords:
- LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
ms.openlocfilehash: bedf96262944d59737a39a942021cdec9445f3b8
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990946"
---
# <a name="linker-tools-error-lnk1256"></a>Chyba linkerů LNK1256

Operace ALINK selhala: důvod

Běžným důvodem pro LINKERŮ LNK1256 je nesprávné číslo verze pro sestavení. Hodnota 65535 není povolena pro žádnou část čísla verze sestavení. Platný rozsah pro verze sestavení je 0-65534.

LINKERŮ LNK1256 může být také způsobena tím, že ALINK nepodařilo najít pojmenovaný kontejner klíčů. Odstraňte kontejner klíčů a znovu ho přidejte do zprostředkovatele CSP se silným názvem pomocí programu [sn. exe (Nástroj pro silný název)](/dotnet/framework/tools/sn-exe-strong-name-tool).

Dalším důvodem pro LINKERŮ LNK1256 je neshoda verzí mezi linkerem a ALink. dll. To může být způsobeno poškozenou instalací sady Visual Studio. Pomocí **programů a funkcí** v Ovládacích panelech systému Windows opravte nebo přeinstalujte sadu Visual Studio.

Následující ukázka generuje LINKERŮ LNK1256:

```cpp
// LNK1256.cpp
// compile with: /clr /LD
// LNK1256 expected
[assembly:System::Reflection::AssemblyVersionAttribute("1.0.65535")];
public class CMyClass {
public:
   int value;
};
```
