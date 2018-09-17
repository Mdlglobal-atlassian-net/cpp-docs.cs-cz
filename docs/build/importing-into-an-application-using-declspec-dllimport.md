---
title: Import do aplikace pomocí __declspec(dllimport) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- __declspec
- dllimport
dev_langs:
- C++
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08a406c8884cdcb9d4b2ead2e61d416ac580fd73
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704079"
---
# <a name="importing-into-an-application-using-declspecdllimport"></a>Import do aplikace s použitím deklarace __declspec(dllimport)

Program, který používá veřejné symboly definované knihovnou DLL se říká, že je importovat. Když vytvoříte soubory hlaviček pro aplikace, které používají vaše DLL knihovny k sestavení, použijte **__declspec(dllimport)** deklarace veřejných symbolů. Klíčové slovo **__declspec(dllimport)** funguje, jestli exportujete pomocí souborů .def nebo se **__declspec(dllexport)** – klíčové slovo.

Aby byl kód čitelnější, definujte makro pro **__declspec(dllimport)** a poté použijte makro k deklaraci každý importovaný symbol:

```
#define DllImport   __declspec( dllimport )

DllImport int  j;
DllImport void func();
```

Pomocí **__declspec(dllimport)** je volitelné na deklarace funkcí, ale kompilátor vytvoří kód efektivnější, pokud použijete toto klíčové slovo. Nicméně je nutné použít **__declspec(dllimport)** pro import spustitelného souboru pro přístup k veřejné datové symboly a objekty knihovny DLL. Všimněte si, že uživatelé vaše knihovna DLL stále nutné propojení s knihovnou importu.

Můžete stejného souboru hlavičky pro knihovnu DLL a klientské aplikace. K tomuto účelu použijte speciální symbol preprocesoru, který označuje, zda je vytváření knihovny DLL nebo vytváření klientské aplikace. Příklad:

```
#ifdef _EXPORTING
   #define CLASS_DECLSPEC    __declspec(dllexport)
#else
   #define CLASS_DECLSPEC    __declspec(dllimport)
#endif

class CLASS_DECLSPEC CExampleA : public CObject
{ ... class definition ... };
```

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Inicializace knihovny DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Import a export vložených funkcí](../build/importing-and-exporting-inline-functions.md)

- [Vzájemné importy](../build/mutual-imports.md)

## <a name="see-also"></a>Viz také

[Import do aplikace](../build/importing-into-an-application.md)