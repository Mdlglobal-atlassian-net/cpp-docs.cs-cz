---
title: Vzájemné importy
ms.date: 11/04/2016
helpviewer_keywords:
- mutual DLL imports [C++]
- AFX_DATA
- importing DLLs [C++], mutual imports
- mutually importing executable files [C++]
- AFX_EXT_CLASS macro
- circular imports
- _AFXEXT preprocessor symbol
- DLLs [C++], importing
- executable files [C++], importing
- extension DLLs [C++], mutual imports
- exporting DLLs [C++], mutual imports
ms.assetid: 2cc29537-92ee-4d92-af39-8b8b3afd808f
ms.openlocfilehash: f01e69138a6ca1744645a1c2fa8525b7088e260d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295674"
---
# <a name="mutual-imports"></a>Vzájemné importy

Export nebo import do jiného spustitelného souboru představuje komplikace, když jsou importy vzájemné (nebo cyklické). Například dvě knihovny DLL importují mezi sebou symboly podobně jako vzájemně rekurzivní funkce.

Problém se vzájemně se importem spustitelných souborů (obvykle knihoven DLL) je, že ani nelze sestavit, aniž by bylo nutné sestavit druhé. Každý proces sestavení vyžaduje jako vstup knihovnu importu vytvořenou jiným procesem sestavení.

Řešením je použití nástroje LIB s možností/DEF, která vytvoří knihovnu importu bez vytváření spustitelného souboru. Pomocí tohoto nástroje můžete vytvořit všechny knihovny pro import, které potřebujete, bez ohledu na to, kolik knihoven DLL je zapojeno nebo jak složité jsou závislosti.

Obecným řešením pro zpracování vzájemného importu je:

1. Každou knihovnu DLL si zase udělejte. (Jakékoli pořadí je proveditelné, i když některé objednávky jsou lépe optimální.) Pokud všechny potřebné knihovny importů existují a jsou aktuální, spusťte odkaz pro sestavení spustitelného souboru (DLL). Tím se vytvoří knihovna importů. V opačném případě spusťte LIB k výrobě knihovny importů.

   Spuštěním knihovny LIB s možností/DEF se vytvoří další soubor s příponou. EXP – rozšíření. Okně. Soubor EXP se musí použít později k sestavení spustitelného souboru.

1. Po použití propojení nebo LIB k sestavení všech knihoven importu, vraťte se a spusťte odkaz a sestavte všechny spustitelné soubory, které nebyly vytvořeny v předchozím kroku. Všimněte si, že odpovídající soubor. exp musí být zadán na lince LINK.

   Pokud jste dříve spustili nástroj LIB a vytvořili knihovnu importu pro DLL1, LIB by vytvořila také soubor DLL1. exp. K propojení při sestavování DLL1. dlll musíte použít DLL1. exp jako vstup.

Následující ilustrace znázorňuje řešení pro dva oboustranné importování knihoven DLL, DLL1 a DLL2. Krok 1: spuštění knihovny LIB se sadou možností/DEF v DLL1. Krok 1 vytvoří DLL1. lib, knihovnu importu a DLL1. exp. V kroku 2 se knihovna importů používá k sestavování DLL2, které zase vytváří knihovnu importu pro symboly DLL2's. Krok 3 sestaví DLL1 pomocí DLL1. exp a DLL2. lib jako vstup. Všimněte si, že soubor. exp pro DLL2 není nutný, protože LIB nebyl použit k sestavení knihovny importu DLL2's.

![Použití vzájemného importu k propojení dvou knihoven DLL](media/vc37yj1.gif "pomocí vzájemného importu k propojení dvou knihoven DLL")<br/>
Propojení dvou knihoven DLL se vzájemnými importy

## <a name="limitations-of-_afxext"></a>Omezení _AFXEXT

Můžete použít `_AFXEXT` symbol preprocesoru pro knihovny DLL rozšíření knihovny MFC, pokud nemáte více vrstev knihoven DLL rozšíření MFC. Máte-li knihovny DLL rozšíření MFC, které volají nebo jsou odvozeny z tříd ve vlastních knihovnách DLL knihovny MFC, které jsou poté odvozeny z tříd knihovny MFC, je nutné použít vlastní symbol preprocesoru, aby nedocházelo k nejednoznačnosti.

Problém je, že v systému Win32 je nutné explicitně deklarovat jakákoli data jako **__declspec (dllexport)** , pokud má být exportována z knihovny DLL, a **__declspec (dllimport)** , pokud má být importována z knihovny DLL. Při definování `_AFXEXT`se v hlavičkách MFC ujistěte, že je správně definovaná **AFX_EXT_CLASS** .

Máte-li více vrstev, jeden symbol jako **AFX_EXT_CLASS** není dostatečný, protože rozšiřující knihovna MFC DLL může exportovat nové třídy a také importovat jiné třídy z jiné knihovny DLL rozšíření knihovny MFC. Chcete-li tento problém vyřešit, použijte speciální symbol preprocesoru, který označuje, že vytváříte vlastní knihovnu DLL proti použití knihovny DLL. Představte si například dvě rozšiřující knihovny MFC DLL, knihovny DLL a B. dll. Každá z nich vyexportuje některé třídy v. h a B. h v uvedeném pořadí. B. dll používá třídy z knihovny DLL. Hlavičkové soubory by vypadaly přibližně takto:

```
/* A.H */
#ifdef A_IMPL
   #define CLASS_DECL_A   __declspec(dllexport)
#else
   #define CLASS_DECL_A   __declspec(dllimport)
#endif

class CLASS_DECL_A CExampleA : public CObject
{ ... class definition ... };

// B.H
#ifdef B_IMPL
   #define CLASS_DECL_B   __declspec(dllexport)
#else
   #define CLASS_DECL_B   __declspec(dllimport)
#endif

class CLASS_DECL_B CExampleB : public CExampleA
{ ... class definition ... };
...
```

Když je knihovna dll sestavena, je sestavena s `/D A_IMPL` a při sestavení B. dll je sestavena s `/D B_IMPL`. Použití samostatných symbolů pro každou knihovnu DLL `CExampleB` je exportováno a `CExampleA` importováno při sestavování B. dll. `CExampleA`je exportována při sestavování souboru. dll a importována při použití B. dll (nebo jiného klienta).

Tento typ vrstvení nelze provést při použití předdefinovaných **AFX_EXT_CLASS** a `_AFXEXT` symbolů preprocesoru. Výše popsaná technika tento problém vyřeší způsobem, který se neshoduje s mechanismem, který samotný vlastní technologie MFC používá při sestavování jeho aktivních technologií, databází a rozšíření knihoven DLL pro rozšíření MFC sítě.

## <a name="not-exporting-the-entire-class"></a>Neexportování celé třídy

Pokud neexportujete celou třídu, je nutné zajistit, aby byly potřebné datové položky vytvořené makry MFC exportovány správně. To lze provést pomocí definice `AFX_DATA` na makro konkrétní třídy. To by mělo být provedeno kdykoli, když celou třídu neexportujete.

Příklad:

```
/* A.H */
#ifdef A_IMPL
   #define CLASS_DECL_A  _declspec(dllexport)
#else
   #define CLASS_DECL_A  _declspec(dllimport)
#endif

#undef  AFX_DATA
#define AFX_DATA CLASS_DECL_A

class CExampleA : public CObject
{
   DECLARE_DYNAMIC()
   CLASS_DECL_A int SomeFunction();
   //... class definition ...
};

#undef AFX_DATA
#define AFX_DATA
```

### <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL](exporting-from-a-dll.md)

- [Exportujte z knihovny DLL pomocí. Soubory DEF](exporting-from-a-dll-using-def-files.md)

- [Export z knihovny DLL pomocí __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Export a import pomocí AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Určení metody exportu, která se má použít](determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

### <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Nástroj LIB a možnost/DEF](reference/lib-reference.md)

## <a name="see-also"></a>Viz také

[Import a export](importing-and-exporting.md)
