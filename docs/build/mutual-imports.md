---
title: "Vzájemné importy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 65b930cece9dd940da3171811fb027fccc3074b6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mutual-imports"></a>Vzájemné importy
Export a import do jiného spustitelného souboru představuje komplikace, když jsou importy vzájemné (nebo cyklické). Například dvě knihovny importovat symboly od sebe navzájem, podobně jako vzájemně rekurzivní funkce.  
  
 Problém s vzájemný import spustitelných souborů (obvykle DLL) je, že ani jeden z nich se dají vytvářet bez vytváření dalších první. Každý proces sestavení vyžaduje jako vstup, knihovnu importu vyprodukované jiného procesu sestavení.  
  
 Řešení je třeba použít nástroj LIB s možností/DEF, která vytváří knihovnu importu bez vytváření spustitelný soubor. Pomocí tohoto nástroje, můžete vytvořit všech knihoven importovat budete potřebovat, bez ohledu na to, kolik knihovny DLL se podílejí nebo jak složitá jsou závislosti.  
  
 Obecné řešení pro zpracování vzájemné importy je:  
  
1.  Naopak trvat každou knihovnu DLL. (Všechny pořadí je to vhodné, i když některé objednávky více optimální.) Pokud všechny potřebné importovanými knihovnami existují a jsou aktuální, spusťte odkaz na sestavení spustitelného souboru (DLL). To vytváří knihovnu importu. Jinak spusťte LIB k vytvoření knihovnu importu.  
  
     Spuštění knihovny LIB s parametrem/DEF vytvoří další soubor s. EXP rozšíření. Na. EXP soubor musí později použít k vytvoření spustitelného souboru.  
  
2.  Po použití odkaz nebo LIB k sestavení všech knihoven importovat, přejděte zpět a spusťte odkaz na sestavení všech spustitelných souborů, které nebyly vytvořené v předchozím kroku. Všimněte si, že musí být zadán odpovídající soubor .exp na řádku odkaz.  
  
     Spustíte-nástroj LIB dříve k vytvoření knihovnu importu pro DLL1, by je tvořen souboru DLL1.exp i LIB. Při sestavování DLL1.dlll, je nutné použít DLL1.exp jako vstup pro odkaz.  
  
 Následující obrázek znázorňuje řešení pro dvě vzájemně import knihoven DLL DLL1 a DLL2. Krok 1 je spustit LIB s nastavenou možností/DEF na DLL1. Krok 1 vytvoří DLL1.lib knihovnu importu a DLL1.exp. V kroku 2 knihovny importu slouží k vytvoření DLL2, což postupně vytvoří knihovnu importu pro symboly DLL2. Krok 3 vytvoří DLL1 pomocí DLL1.exp a DLL2.lib jako vstup. Všimněte si, že soubor .exp pro DLL2 není nezbytné, protože LIB nebyl použit pro sestavení knihovny importu DLL2.  
  
 ![Vzájemné importy pomocí propojení dvou knihoven DLL](../build/media/vc37yj1.gif "vc37YJ1")  
Propojení dvou knihoven DLL se vzájemné importy  
  
## <a name="limitations-of-afxext"></a>Omezení _AFXEXT  
 Můžete použít `_AFXEXT` – symbol preprocesoru pro vaše MFC – rozšiřující knihovny DLL, pokud nemáte více vrstev MFC – rozšiřující knihovny DLL. Pokud máte MFC – rozšiřující knihovny DLL, které volají nebo odvozena od třídy ve vlastních MFC – rozšiřující knihovny DLL, které pak odvozena od třídy MFC, musíte použít vlastní – symbol preprocesoru aby se zabránilo nejednoznačnosti.  
  
 Problém je, že v Win32, musí explicitně deklarovat všechna data jako **__declspec(dllexport)** Pokud mají být exportovány z knihovny DLL, a **deklarace __declspec(dllimport)** má-li importovat z knihovny DLL. Když definujete `_AFXEXT`, hlavičky knihovny MFC Ujistěte se, že **AFX_EXT_CLASS** správnou definici.  
  
 Pokud máte více vrstev, jeden symbol, jako **AFX_EXT_CLASS** nestačí, protože knihovnu DLL může exportovat nové třídy, jako jako importovat jiné třídy z jiné MFC – rozšiřující knihovny DLL. Chcete-li tento problém vyřešit, použijte speciální symbol preprocesoru, která určuje, že vytváříte samotné knihovny DLL a kdy knihovnu DLL. Představte si například dvě MFC rozšiřující knihovny DLL, A.dll a B.dll. Každá exportovat některé třídy v A.h B.h.. B.dll používá třídy z A.dll. Soubory hlaviček by vypadat přibližně takto:  
  
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
  
 Když je A.dll sestavena, je sestavena s `/D A_IMPL` a když je B.dll sestavena, je sestavena s `/D B_IMPL`. Použitím oddělených symbolů pro každou knihovnu DLL, `CExampleB` se exportují a `CExampleA` je importován při vytváření B.dll. `CExampleA`je exportována při vytváření A.dll a importován při použití B.dll (nebo jiného klienta).  
  
 Tento typ vrstvení nelze provést, pokud používáte integrované **AFX_EXT_CLASS** a `_AFXEXT` preprocesoru symboly. Technik popsaných výše řeší tento problém není na rozdíl od způsobem mechanismus MFC samotné používá při sestavování jeho Active technologie, databáze a sítě MFC – knihovny DLL rozšíření.  
  
## <a name="not-exporting-the-entire-class"></a>Export není celý – třída  
 Pokud neexportujete celou třídu, budete muset zajistit, aby nezbytné datové položky vytvořené makry MFC jsou exportovány správně. Můžete to provést opětovná definice `AFX_DATA` na makro konkrétní třídy. To by mělo být provedeno kdykoli neexportujete celou třídu.  
  
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
  
-   [Export z knihovny DLL](../build/exporting-from-a-dll.md)  
  
-   [Export z knihovny DLL pomocí. DEF soubory](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Export z knihovny DLL pomocí deklarace __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Export a import pomocí třídy AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Určení použité metody exportu](../build/determining-which-exporting-method-to-use.md)  
  
-   [Import do aplikace pomocí deklarace __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Nástroj LIB a možnost/DEF](../build/reference/lib-reference.md)  
  
## <a name="see-also"></a>Viz také  
 [Import a export](../build/importing-and-exporting.md)