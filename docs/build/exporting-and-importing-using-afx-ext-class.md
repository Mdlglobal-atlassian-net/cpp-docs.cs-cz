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

[Knihovny DLL rozšíření knihovny MFC](extension-dlls-overview.md) používají k exportu tříd **AFX_EXT_CLASS** maker. Spustitelné soubory, které odkazují na knihovnu DLL rozšíření knihovny MFC, používají makro k importu tříd. S **AFX_EXT_CLASS** makro, stejné soubory hlaviček, které se používají k vytvoření knihovny DLL rozšíření knihovny MFC lze použít s spustitelné soubory, které odkazují na knihovnu DLL.

V souboru záhlaví pro dll přidejte klíčové slovo **AFX_EXT_CLASS** do deklarace třídy takto:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Toto makro je definováno knihovnou MFC jako `__declspec(dllexport)` při symbolech preprocesoru a `_AFXDLL` `_AFXEXT` jsou definovány. Makro je však `__declspec(dllimport)` `_AFXDLL` definováno `_AFXEXT` jako kdy je definováno a není definováno. Pokud je definována, `_AFXDLL` symbol preprocesoru označuje, že sdílená verze knihovny MFC je používána cílovým spustitelným souborem (knihovnou DLL nebo aplikací). Pokud `_AFXDLL` jsou `_AFXEXT` definovány oba a jsou definovány, znamená to, že cílový spustitelný soubor je knihovna DLL rozšíření knihovny MFC.

Protože `AFX_EXT_CLASS` je `__declspec(dllexport)` definována jako při exportu z knihovny DLL rozšíření knihovny MFC, můžete exportovat celé třídy bez umístění dekorovaných názvů pro všechny symboly této třídy v souboru .def.

I když se můžete vyhnout vytváření souboru .def a všechny dekorované názvy pro třídu s touto metodou, vytvoření souboru .def je efektivnější, protože názvy lze exportovat podle ordinalu. Chcete-li použít metodu exportu souboru DEF, umístěte na začátek a konec souboru záhlaví následující kód:

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
> Při exportu vslaných funkcí buďte opatrní, protože mohou vytvářet možnost konfliktů verzí. Funkce inline se rozbalí do kódu aplikace; Proto pokud později přepsat funkci, není získat aktualizovány, pokud samotná aplikace je znovu zkompilován. Za normálních okolností dll funkce lze aktualizovat bez opětovného sestavení aplikace, které je používají.

## <a name="exporting-individual-members-in-a-class"></a>Export jednotlivých členů ve třídě

Někdy můžete chtít exportovat jednotlivé členy třídy. Například pokud exportujete `CDialog`odvozenou třídu, budete muset exportovat pouze `DoModal` konstruktor a volání. Můžete použít `AFX_EXT_CLASS` na jednotlivé členy, které potřebujete exportovat.

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

Vzhledem k tomu, že již exportujete všechny členy třídy, může dojít k dalšímu problému z důvodu způsobu, jakým makra knihovny MFC fungují. Několik pomocných maker knihovny MFC skutečně deklaruje nebo definuje datové členy. Proto musí být tyto datové členy také exportovány z dll.

Makro je `DECLARE_DYNAMIC` například definováno takto při vytváření knihovny DLL rozšíření knihovny MFC:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

Řádek, který začíná `AFX_DATA` statickou, deklaruje statický objekt uvnitř třídy. Chcete-li tuto třídu správně exportovat a získat přístup k informacím za běhu ze spustitelného souboru klienta, je nutné exportovat tento statický objekt. Vzhledem k tomu, že `AFX_DATA`statický objekt je `AFX_DATA` deklarován s modifikátorem , stačí definovat být `__declspec(dllexport)` při vytváření knihovny DLL a definovat ji jako `__declspec(dllimport)` při vytváření spustitelného souboru klienta. Protože `AFX_EXT_CLASS` je již definována tímto způsobem, `AFX_DATA` stačí předefinovat `AFX_EXT_CLASS` být stejný jako kolem definice třídy.

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

Vzhledem k tomu, že knihovna `AFX_DATA` MFC vždy používá symbol na datových položkách, které definuje v rámci svých maker, tato technika funguje pro všechny takové scénáře. Například, to `DECLARE_MESSAGE_MAP`funguje pro .

> [!NOTE]
> Pokud exportujete celou třídu, nikoli vybrané členy třídy, budou automaticky exportovány statické datové členy.

### <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z dll pomocí souborů .def](exporting-from-a-dll-using-def-files.md)

- [Export z dll pomocí __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Export funkcí Jazyka C pro použití ve spustitelných souborech jazyka C nebo C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Určení metody exportu, která se má použít](determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicializovat dll](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>O čem chcete vědět více?

- [Dekorované názvy](reference/decorated-names.md)

- [Import a export vřádkových funkcí](importing-and-exporting-inline-functions.md)

- [Vzájemné dovozy](mutual-imports.md)

## <a name="see-also"></a>Viz také

[Export z knihovny DLL](exporting-from-a-dll.md)
