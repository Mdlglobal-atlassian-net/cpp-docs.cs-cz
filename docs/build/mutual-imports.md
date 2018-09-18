---
title: Vzájemné importy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7aee01e72fb8386b6aee7e6a505424b4138f45d7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704838"
---
# <a name="mutual-imports"></a>Vzájemné importy

Export a import do jiného spustitelného souboru představuje komplikace, když jsou importy vzájemné (nebo cyklické). Například dvě knihovny importu symboly od sebe navzájem, podobný vzájemně rekurzivní funkce.

Problém s vzájemný import spustitelných souborů (obvykle knihovny DLL) je, že ani jeden může být sestaven bez sestavení jiné první. Každý proces sestavení vyžaduje jako vstup, knihovnu importu vytvořený jiným procesem sestavení.

Řešením je použít nástroj LIB s def možnost, která vytvoří knihovnu importu bez vytváření spustitelného souboru. Pomocí tohoto nástroje můžete vytvořit všechny potřebné knihovny importu potřebujete, bez ohledu na to, kolik knihovny DLL se podílejí nebo jak složitou jsou závislosti.

Obecné řešení pro zpracování vzájemné importy je:

1. Pak provést každou knihovnu DLL. (Žádné pořadí je to možné, i když některé příkazy jsou více optimální.) Pokud všechny potřebné importu knihovny existují a jsou aktuální, spusťte odkaz na sestavení spustitelného souboru (DLL). Tímto se vytvoří knihovnu importu. V opačném případě spusťte nástroj LIB vytvoří knihovnu importu.

   Spuštění knihovny LIB se parametr/DEF vytvoří další soubor s. EXP rozšíření. Na. EXP souboru musíte později použít k sestavení spustitelného souboru.

1. Po použití odkazu nebo LIB k sestavení všech knihoven, import, přejděte zpět a spusťte odkaz na sestavení žádné spustitelné soubory, které nebyly vytvořeny v předchozím kroku. Všimněte si, že odpovídající souboru .exp musí být zadán v řádku propojení.

   Pokud se má spustit nástroj LIB dříve k vytvoření knihovnu importu pro DLL1, LIB by vytvořil soubor DLL1.exp také. Při sestavování DLL1.dlll, je nutné použít DLL1.exp jako vstup pro propojení.

Následující obrázek znázorňuje řešení pro dva vzájemně importu knihovny DLL, DLL1 a DLL2. Krok 1 je ke spuštění knihovny LIB, sadou def – možnost na DLL1. Krok 1 vytváří DLL1.lib knihovnu importu a DLL1.exp. V kroku 2 knihovnu importu se používá k vytvoření DLL2, které pak vytvoří knihovnu importu DLL2 symbolů. Krok 3 sestavení DLL1 pomocí DLL1.exp a DLL2.lib jako vstup. Všimněte si, že soubor s .exp DLL2 není nezbytné, protože LIB nebyl použit k sestavení knihovny importu DLL2.

![Vzájemné importy pomocí propojení dvou knihovny DLL](../build/media/vc37yj1.gif "propojit dvě knihovny DLL pomocí vzájemné importy")<br/>
Propojení dvou knihoven DLL s vzájemné importy

## <a name="limitations-of-afxext"></a>Omezení _AFXEXT

Můžete použít `_AFXEXT` symbol preprocesoru pro vaše MFC – rozšiřující knihovny DLL, pokud nemáte více vrstev MFC – rozšiřující knihovny DLL. Pokud máte MFC – rozšiřující knihovny DLL, které volají nebo jsou odvozeny z tříd ve vlastním MFC – rozšiřující knihovny DLL, které pak jsou odvozeny z třídy knihovny MFC, musíte použít vlastní symbol preprocesoru Chcete-li předejít nejednoznačnosti.

V čem problém spočívá tohoto v systému Win32, musíte explicitně deklarovat všechna data jako **__declspec(dllexport)** pokud export z knihovny DLL, a **__declspec(dllimport)** Pokud má být importována z knihovny DLL. Při definování `_AFXEXT`, hlaviček knihovny MFC, zkontrolujte, zda **AFX_EXT_CLASS** je správně definován.

Pokud máte více vrstev, jeden symbol, jako **AFX_EXT_CLASS** nestačí, protože rozšiřující knihovny DLL MFC může exportovat nové třídy, jak jako import jiné třídy z jiného MFC – rozšiřující knihovny DLL. Pokud chcete tento problém vyřešit, použijte speciální symbol preprocesoru, který označuje, že vytváříte samotná knihovna DLL oproti použití knihovny DLL. Představte si například dvě rozšiřující knihovny DLL MFC, A.dll a B.dll. Každá exportovat některé třídy v A.h B.h. B.dll používá třídy z A.dll. Soubory hlaviček by vypadat přibližně takto:

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

Při vytváření A.dll, je sestavena s `/D A_IMPL` a při vytváření B.dll, je sestavena s `/D B_IMPL`. Pomocí samostatných symbolů pro každou knihovnu DLL `CExampleB` exportu a `CExampleA` je importován při vytváření B.dll. `CExampleA` Při exportu při sestavování A.dll a importován při použití B.dll (nebo jiného klienta).

Tento typ vrstvení nelze provést, při použití předdefinované **AFX_EXT_CLASS** a `_AFXEXT` symboly preprocesoru. Tento problém není na rozdíl od způsobem mechanismus knihovna MFC sama používá při vytváření Active technologie, databáze a rozšiřující knihovny DLL MFC sítě řeší techniky popsané výše.

## <a name="not-exporting-the-entire-class"></a>Export není celé třídy

Pokud neexportujete celou třídu, budete muset Ujistěte se, že jsou správně exportovány potřebná data položky vytvořené pomocí maker knihovny MFC. Můžete to provést, nově definují obor `AFX_DATA` makra určité třídy. To by mělo být provedeno kdykoli neexportujete celá třída.

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

- [Export z knihovny DLL](../build/exporting-from-a-dll.md)

- [Export z knihovny DLL pomocí. DEF soubory](../build/exporting-from-a-dll-using-def-files.md)

- [Export z knihovny DLL pomocí __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Export a import pomocí AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Určit, kterou exportovací metodu použít](../build/determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Nástroj LIB a parametr/def](../build/reference/lib-reference.md)

## <a name="see-also"></a>Viz také

[Import a export](../build/importing-and-exporting.md)