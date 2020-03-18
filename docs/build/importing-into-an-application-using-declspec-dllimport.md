---
title: Import do aplikace s použitím deklarace __declspec(dllimport)
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
ms.openlocfilehash: fd7d42ec5a76b92aa789a3a20f38e6b2c0fd2cb1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440409"
---
# <a name="import-into-an-application-using-__declspecdllimport"></a>Import do aplikace s použitím deklarace __declspec(dllimport)

Program, který používá veřejné symboly definované knihovnou DLL, je uveden pro import. Při vytváření hlavičkových souborů pro aplikace, které používají knihovny DLL k sestavení pomocí, použijte **__declspec (dllimport)** pro deklarace veřejných symbolů. Klíčové slovo **__declspec (dllimport)** funguje bez ohledu na to, zda exportujete do souborů. def nebo pomocí klíčového slova **__declspec (dllexport)** .

Aby byl váš kód čitelnější, definujte makro pro **__declspec (dllimport)** a pak použijte makro k deklaraci každého importovaného symbolu:

```
#define DllImport   __declspec( dllimport )

DllImport int  j;
DllImport void func();
```

Použití **__declspec (dllimport)** je volitelné v deklaracích funkcí, ale kompilátor vytváří efektivnější kód, pokud použijete toto klíčové slovo. Je však nutné použít **__declspec (dllimport)** pro import spustitelného souboru pro přístup ke symbolům a objektům veřejných dat knihovny DLL. Všimněte si, že uživatelé vaší knihovny DLL stále musí propojit knihovnu importů.

Můžete použít stejný hlavičkový soubor pro knihovnu DLL i pro klientskou aplikaci. K tomu použijte speciální symbol preprocesoru, který označuje, zda vytváříte knihovnu DLL nebo vytváříte klientskou aplikaci. Příklad:

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

- [Inicializovat knihovnu DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Import a export vložených funkcí](importing-and-exporting-inline-functions.md)

- [Vzájemné importy](mutual-imports.md)

## <a name="see-also"></a>Viz také

[Import do aplikace](importing-into-an-application.md)
