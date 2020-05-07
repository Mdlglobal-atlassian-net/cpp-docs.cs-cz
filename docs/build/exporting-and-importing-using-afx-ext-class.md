---
title: Export a import pomocí třídy AFX_EXT_CLASS
ms.date: 11/04/2016
f1_keywords:
- afx_ext_class
helpviewer_keywords:
- AFX_EXT_CLASS macro
- exporting classes [C++]
- importing DLLs [C++]
- extension DLLs [C++], exporting classes
- executable files [C++], importing classes
- exporting DLLs [C++], AFX_EXT_CLASS macro
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
ms.openlocfilehash: 95c72f8251a8a59833483eb948709c80a69d03d7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328601"
---
# <a name="exporting-and-importing-using-afx_ext_class"></a>Export a import pomocí třídy AFX_EXT_CLASS

[Knihovny DLL rozšíření MFC](extension-dlls-overview.md) používají **AFX_EXT_CLASS** makra k exportu tříd; spustitelné soubory, které odkazují na rozšiřující DLL knihovny MFC, používají makro pro Import tříd. Pomocí makra **AFX_EXT_CLASS** lze použít stejné hlavičkové soubory, které jsou použity k sestavení knihovny DLL rozšíření MFC, pomocí spustitelných souborů, které odkazují na knihovnu DLL.

V hlavičkovém souboru pro knihovnu DLL přidejte klíčové slovo **AFX_EXT_CLASS** k deklaraci vaší třídy následujícím způsobem:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Toto makro je definováno knihovnou MFC `__declspec(dllexport)` jako při definování symbolů `_AFXDLL` preprocesoru a `_AFXEXT` . Ale makro je definováno jako `__declspec(dllimport)` , když `_AFXDLL` je definováno a `_AFXEXT` není definováno. Je-li definován, symbol `_AFXDLL` preprocesoru označuje, že sdílená verze knihovny MFC je používána cílovým spustitelným souborem (buď knihovnou DLL, nebo aplikací). Pokud jsou `_AFXDLL` definovány `_AFXEXT` a, znamená to, že cílový spustitelný soubor je knihovna DLL rozšíření MFC.

Protože `AFX_EXT_CLASS` je definována jako `__declspec(dllexport)` při exportu z rozšiřující knihovny MFC knihovny MFC, můžete exportovat celé třídy bez umístění dekorované názvy pro všechny symboly této třídy v souboru. def.

I když se můžete vyhnout vytváření souboru. def a všech dekorovaných názvů třídy touto metodou, vytvoření souboru. def je efektivnější, protože názvy lze exportovat podle pořadového čísla. Chcete-li použít metodu. def souboru pro export, vložte následující kód na začátek a konec hlavičkového souboru:

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
> Při exportu vložených funkcí buďte opatrní, protože mohou vytvořit možnost konfliktu verzí. Vložená funkce se rozšíří do kódu aplikace; Proto pokud později znovu zapíšete funkci, nebude aktualizována, pokud aplikace samotná nebude znovu zkompilována. Normálně lze funkce knihoven DLL aktualizovat bez nutnosti znovu sestavovat aplikace, které je používají.

## <a name="exporting-individual-members-in-a-class"></a>Export jednotlivých členů ve třídě

Někdy je vhodné exportovat jednotlivé členy vaší třídy. Například pokud exportujete `CDialog`třídu odvozenou od třídy, může být nutné exportovat pouze konstruktor a `DoModal` volání. Můžete použít `AFX_EXT_CLASS` na jednotlivých členech, které potřebujete exportovat.

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

Vzhledem k tomu, že již neexportujete všechny členy třídy, může dojít k dalšímu problému, protože makra knihovny MFC fungují. Několik pomocných maker knihovny MFC aktuálně deklaruje nebo definuje datové členy. Proto musí být tyto datové členy také exportovány z vaší knihovny DLL.

Například `DECLARE_DYNAMIC` makro je definováno následujícím způsobem při vytváření rozšiřující knihovny MFC DLL:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

Řádek, který začíná se statickým `AFX_DATA` , deklaruje statický objekt uvnitř vaší třídy. Chcete-li tuto třídu správně exportovat a získat přístup k běhovým informacím z klientského spustitelného souboru, je nutné tento statický objekt exportovat. Vzhledem k tomu, že statický objekt je deklarován `AFX_DATA`s modifikátorem, je třeba `AFX_DATA` definovat, `__declspec(dllexport)` aby bylo sestavení knihovny DLL a definováno jako `__declspec(dllimport)` při vytváření spustitelného souboru klienta. Vzhledem `AFX_EXT_CLASS` k tomu, že je již definován tímto způsobem, stačí předefinovat `AFX_DATA` , aby bylo stejné jako `AFX_EXT_CLASS` kolem definice vaší třídy.

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

Protože knihovna MFC vždy používá `AFX_DATA` symbol pro položky dat, které definuje v rámci svých maker, tato technika funguje pro všechny takové scénáře. Například funguje pro `DECLARE_MESSAGE_MAP`.

> [!NOTE]
> Pokud exportujete celou třídu namísto vybraných členů třídy, statické datové členy budou automaticky exportovány.

### <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL pomocí souborů. def](exporting-from-a-dll-using-def-files.md)

- [Export z knihovny DLL pomocí __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Určení metody exportu, která se má použít](determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicializovat knihovnu DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Dekorované názvy](reference/decorated-names.md)

- [Import a export vložených funkcí](importing-and-exporting-inline-functions.md)

- [Vzájemné importy](mutual-imports.md)

## <a name="see-also"></a>Viz také

[Export z knihovny DLL](exporting-from-a-dll.md)
