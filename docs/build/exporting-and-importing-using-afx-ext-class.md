---
title: Export a import pomocí AFX_EXT_CLASS | Dokumentace Microsoftu
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
ms.openlocfilehash: 46964b4babc7d7afd4b523ee37981296e9f7dc57
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711932"
---
# <a name="exporting-and-importing-using-afxextclass"></a>Export a import pomocí třídy AFX_EXT_CLASS

[MFC – rozšiřující knihovny DLL](../build/extension-dlls-overview.md) použijte makro **AFX_EXT_CLASS** export tříd; spustitelné soubory, které jsou propojeny do MFC – rozšiřující knihovny DLL použijte makro postup importu tříd. S **AFX_EXT_CLASS** – makro, stejné soubory hlaviček, které se používají k vytvoření MFC – rozšiřující knihovny DLL lze použít s spustitelné soubory, které odkazují na knihovny DLL.

V souboru hlaviček pro vaši knihovnu DLL, přidejte **AFX_EXT_CLASS** – klíčové slovo k deklaraci vaší třídy následujícím způsobem:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Toto makro je definováno v prostředí MFC jako `__declspec(dllexport)` při symboly preprocesoru `_AFXDLL` a `_AFXEXT` jsou definovány. Ale makro je definováno jako `__declspec(dllimport)` při `_AFXDLL` je definována a `_AFXEXT` není definován. Při definování symbol preprocesoru `_AFXDLL` označuje, že používá sdílenou verzi knihovny MFC cílový spustitelný soubor (knihovny DLL nebo aplikaci). Pokud obě `_AFXDLL` a `_AFXEXT` jsou definovány, to znamená, že cílový spustitelný soubor je rozšiřující knihovny DLL MFC.

Protože `AFX_EXT_CLASS` je definován jako `__declspec(dllexport)` při exportu ze rozšiřující knihovny DLL MFC, můžete exportovat celé třídy bez uvedení v .def souboru dekorované názvy pro všechny symboly dané třídy.

I když se vytváří soubor .def a všechny dekorované názvy pro třídu s touto metodou se můžete vyhnout, je vytvoření souboru .def mnohem efektivnější, protože názvy je možné exportovat podle pořadových čísel. Pokud chcete použít metodu .def souboru exportu, umístěte následující kód na začátek a konec souboru záhlaví:

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
>  Buďte opatrní při export vložených funkcí, protože můžou vytvořit možnost konflikty verzí. Vložená funkce se rozbalí do kódu aplikace; Proto pokud později přepsat funkci, se neaktualizuje Pokud samotná aplikace přepsán. Za normálních okolností funkcí knihovny DLL, které je možné aktualizovat bez nutnosti opětovného sestavení aplikace, které je používají.

## <a name="exporting-individual-members-in-a-class"></a>Export jednotlivé členy ve třídě

Někdy můžete chtít exportovat jednotlivé členy třídy. Například, pokud jste exportovali `CDialog`-odvozené třídy, je pouze potřeba vyexportovat konstruktoru a `DoModal` volání. Můžete použít `AFX_EXT_CLASS` u jednotlivých členů, je nutné exportovat.

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

Vzhledem k tomu, že exportujete už všichni členové třídy, můžete jej spustit do další problém vzhledem ke způsobu, které pracují maker knihovny MFC. Některé z makra pomocné rutiny knihovny MFC ve skutečnosti deklarujete nebo definujete datové členy. Proto tyto datové členy musí být také exportován z knihovny DLL.

Například `DECLARE_DYNAMIC` – makro je definovaná následujícím způsobem při sestavování rozšiřující knihovny DLL MFC:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

Řádek, který začíná statické `AFX_DATA` je deklarace statických objektů uvnitř vaší třídy. K exportu této třídy správně a přístup k informacím o za běhu z klienta spustitelný soubor, je nutné exportovat tento statický objekt. Protože má statický objekt je deklarována s modifikátorem `AFX_DATA`, budete muset definovat `AFX_DATA` bude `__declspec(dllexport)` při vytváření knihovny DLL a definujte jej jako `__declspec(dllimport)` při vytváření vašeho klientského spustitelného souboru. Protože `AFX_EXT_CLASS` je už definovaná tímto způsobem, stačí znovu definovat `AFX_DATA` být stejný jako `AFX_EXT_CLASS` kolem vaší definice třídy.

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

Vzhledem k tomu vždy používá MFC `AFX_DATA` symbolu na datových položek definuje v rámci jeho makra, tento postup funguje pro všechny tyto scénáře. Například funguje pro `DECLARE_MESSAGE_MAP`.

> [!NOTE]
>  Chcete-li exportovat celé třídy místo vybrané členy třídy, se automaticky vyexportují statické datové členy.

### <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL pomocí souborů .def](../build/exporting-from-a-dll-using-def-files.md)

- [Export z knihovny DLL pomocí __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo C++ – jazyk](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Určit, kterou exportovací metodu použít](../build/determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

- [Inicializace knihovny DLL](../build/run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Dekorované názvy](../build/reference/decorated-names.md)

- [Import a export vložených funkcí](../build/importing-and-exporting-inline-functions.md)

- [Vzájemné importy](../build/mutual-imports.md)

## <a name="see-also"></a>Viz také

[Export z knihovny DLL](../build/exporting-from-a-dll.md)