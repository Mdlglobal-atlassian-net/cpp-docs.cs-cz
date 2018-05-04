---
title: Export a import pomocí třídy AFX_EXT_CLASS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- afx_ext_class
dev_langs:
- C++
helpviewer_keywords:
- AFX_EXT_CLASS macro
- exporting classes [C++]
- importing DLLs [C++]
- extension DLLs [C++], exporting classes
- executable files [C++], importing classes
- exporting DLLs [C++], AFX_EXT_CLASS macro
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6cc853c66afae72d6e426d800c0443ab206ab20
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="exporting-and-importing-using-afxextclass"></a>Export a import pomocí třídy AFX_EXT_CLASS  
  
[MFC – rozšiřující knihovny DLL](../build/extension-dlls-overview.md) použijte makro **AFX_EXT_CLASS** export tříd, spustitelné soubory, které odkazují MFC – rozšiřující knihovny DLL pomocí makro postup importu tříd. Pomocí **AFX_EXT_CLASS** makro, stejné soubory hlaviček, které se používají k sestavení rozšíření MFC DLL lze použít s spustitelné soubory, které na knihovnu DLL.  
  
 V záhlaví souboru pro knihovny DLL, přidejte **AFX_EXT_CLASS** – klíčové slovo k prohlášení o třídě následujícím způsobem:  
  
```cpp  
class AFX_EXT_CLASS CMyClass : public CDocument  
{  
// <body of class>  
};  
```  
  
Toto makro je definováno v prostředí MFC jako `__declspec(dllexport)` při preprocesoru symboly `_AFXDLL` a `_AFXEXT` jsou definovány. Makro není však definována jako `__declspec(dllimport)` při `_AFXDLL` je definovaný a `_AFXEXT` není definován. Při definování preprocesoru symbol `_AFXDLL` Určuje, že je použit sdílená verze knihovny MFC cílem spustitelného souboru (knihovny DLL nebo aplikace). Pokud obě `_AFXDLL` a `_AFXEXT` jsou definovány, to znamená, že cílový spustitelný soubor je knihovnu DLL.  
  
Protože `AFX_EXT_CLASS` je definován jako `__declspec(dllexport)` při exportu z knihovnu DLL, můžete exportovat celé třídy bez umístění dekorované názvy pro všechny symboly této třídy v souboru .def.  
  
I když vytváření .def soubor a všechny dekorované názvy pro třídu u této metody se můžete vyhnout, je vytvoření souboru .def efektivnější, protože názvy můžete exportovat podle pořadí. Chcete-li použít metodu .def souboru exportu, umístěte následující kód na začátku a konci hlavičkový soubor:  
  
```cpp  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
> [!CAUTION]
>  Buďte opatrní při exportu vložených funkcí, protože mohou vytvářet možné konflikty verzí. Vložená funkce je rozšířena do kódu aplikace; Proto pokud později přepíšete funkce, se neaktualizuje Pokud znovu zkompiluje vlastní aplikace. Za normálních okolností funkcí knihovny DLL lze aktualizovat bez nutnosti opětovného sestavení aplikace, které je používají.  
  
## <a name="exporting-individual-members-in-a-class"></a>Export jednotlivé členy v třídě  
  
V některých případech můžete chtít exportovat jednotlivé členy vaší třídy. Například pokud chcete exportovat `CDialog`-odvozené třídy, můžete potřebovat pouze pro export konstruktoru a `DoModal` volání. Můžete použít `AFX_EXT_CLASS` na jednotlivé členy, je třeba exportovat.  
  
Příklad:  
  
```cpp  
class CExampleDialog : public CDialog  
{  
public:  
   AFX_EXT_CLASS CExampleDialog();  
   AFX_EXT_CLASS int DoModal();  
   ...  
   // rest of class definition  
   ...  
};  
```  
  
Vzhledem k tomu, že už exportujete všichni členové třídy, můžete spustit také do dalšího problému z toho důvodu, které pracují maker MFC. Řadu makra pomocné knihovny MFC ve skutečnosti deklarovat nebo definovat datových členů. Proto je potřeba tyto datové členy také exportovat z knihovny DLL.  
  
Například `DECLARE_DYNAMIC` makro je při sestavování rozšíření MFC DLL definován následujícím způsobem:  
  
```cpp  
#define DECLARE_DYNAMIC(class_name) \  
protected: \  
   static CRuntimeClass* PASCAL _GetBaseClass(); \  
public: \  
   static AFX_DATA CRuntimeClass class##class_name; \  
   virtual CRuntimeClass* GetRuntimeClass() const; \  
```  
  
Řádek, který začíná statické `AFX_DATA` je deklarování statického objektu uvnitř vaší třídy. Pokud chcete exportovat tato třída správně a přistupovat k běhu informace z spustitelný soubor klienta, je nutné exportovat tento statický objekt. Protože je statický objekt je deklarovaný s modifikátorem `AFX_DATA`, potřebujete definovat `AFX_DATA` být `__declspec(dllexport)` při vytváření knihovny DLL a definovat jako `__declspec(dllimport)` při sestavování vašeho klientského spustitelného souboru. Protože `AFX_EXT_CLASS` je již definován tímto způsobem, stačí znovu definovat `AFX_DATA` být stejný jako `AFX_EXT_CLASS` kolem definice vaší třídy.  
  
Příklad:  
  
```cpp  
#undef  AFX_DATA  
#define AFX_DATA AFX_EXT_CLASS  
  
class CExampleView : public CView  
{  
   DECLARE_DYNAMIC()  
   // ... class definition ...  
};  
  
#undef  AFX_DATA  
#define AFX_DATA  
```  
  
Protože MFC vždy používá `AFX_DATA` symbol na datových položek, které definuje v rámci jeho makra funguje tento postup u všech scénářů. Například funguje pro `DECLARE_MESSAGE_MAP`.  
  
> [!NOTE]
>  Pokud chcete exportovat celou třídu místo vybrané členy třídy, exportují se automaticky členy statických dat.  
  
### <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Export z knihovny DLL pomocí souborů .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Export z knihovny DLL pomocí deklarace __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo jazyka C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Určení použité metody exportu](../build/determining-which-exporting-method-to-use.md)  
  
-   [Import do aplikace pomocí deklarace __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicializace knihovny DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Dekorované názvy](../build/reference/decorated-names.md)  
  
-   [Import a export vložených funkcí](../build/importing-and-exporting-inline-functions.md)  
  
-   [Vzájemné importy](../build/mutual-imports.md)  
  
## <a name="see-also"></a>Viz také  
 [Export z knihovny DLL](../build/exporting-from-a-dll.md)