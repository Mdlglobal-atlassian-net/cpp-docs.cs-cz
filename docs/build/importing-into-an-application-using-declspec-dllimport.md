---
title: Import do aplikace s použitím deklarace __declspec(dllimport)
ms.date: 11/04/2016
f1_keywords:
- __declspec
- dllimport
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
ms.openlocfilehash: 30e0f6517f2d749962c5cf49dddb1662c9ccf129
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810221"
---
# <a name="import-into-an-application-using-declspecdllimport"></a>Import do aplikace s použitím deklarace __declspec(dllimport)

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

- [Inicializace knihovny DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Import a export vložených funkcí](importing-and-exporting-inline-functions.md)

- [Vzájemné importy](mutual-imports.md)

## <a name="see-also"></a>Viz také:

[Import do aplikace](importing-into-an-application.md)
