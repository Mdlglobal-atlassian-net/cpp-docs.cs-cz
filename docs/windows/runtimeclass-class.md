---
title: Runtimeclass – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClass class
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8f6cca23834eb889ecb83d91b40861b92fe922ad
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605981"
---
# <a name="runtimeclass-class"></a>RuntimeClass – třída

Představuje třídu WinRT nebo COM, která dědí zadaných rozhraní a poskytuje zadaného modulu Windows Runtime, klasické rozhraní COM a slabou podporu odkazu.

Tato třída poskytuje standardní implementace WinRT a com. tříd, poskytuje implementaci `QueryInterface`, `AddRef`, `Release` atd., spravuje referenčního počtu modulu a obsahuje podporu pro poskytuje objekt pro vytváření tříd pro aktivovatelné objekty.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```

### <a name="parameters"></a>Parametry

*classFlags*  
Volitelný parametr. Kombinace jedné nebo více [runtimeclasstype –](../windows/runtimeclasstype-enumeration.md) hodnot výčtu. `__WRL_CONFIGURATION_LEGACY__` Makra lze definovat za účelem změnit výchozí hodnotu classFlags pro všechny třídy modulu runtime v projektu. Pokud definována, RuntimeClass instance jsou mimo agilní ve výchozím nastavení. Pokud není definován, RuntimeClass instance jsou agilní ve výchozím nastavení. Aby se zabránilo nejednoznačnosti vždy zadávat `Microsoft::WRL::FtmBase` v `TInterfaces` nebo `RuntimeClassType::InhibitFtmBase`. Poznámka: Pokud jsou obě používají objekt InhibitFtmBase a ftmbase – bude agile.

*TInterfaces*  
Seznam rozhraní objekt implementuje nad rámec `IUnknown`, `IInspectable` nebo jiných rozhraní řídí [runtimeclasstype –](../windows/runtimeclasstype-enumeration.md). Je také může seznam jiných tříd nelze odvodit z, zejména `Microsoft::WRL::FtmBase` vytvořit objekt agilní a způsobit, že k implementaci `IMarshal`.

## <a name="members"></a>Členové

`RuntimeClassInitialize` Funkce, která inicializuje objekt, pokud `MakeAndInitialize` šablony funkce se používá ke konstrukci objektu. Vrátí hodnotu S_OK, pokud objekt byl úspěšně inicializován nebo kód chyby modelu COM. Pokud inicializace se nezdařila. Kód chyby modelu COM je postoupena jako návratovou hodnotu `MakeAndInitialize`. Všimněte si, že `RuntimeClassInitialize` metoda není volána, pokud `Make` šablony funkce se používá ke konstrukci objektu.

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[RuntimeClass::RuntimeClass – konstruktor](../windows/runtimeclass-runtimeclass-constructor.md)|Inicializuje aktuální instance třídy RuntimeClass.|
|[RuntimeClass::~RuntimeClass – destruktor](../windows/runtimeclass-tilde-runtimeclass-destructor.md)|Zruší inicializaci aktuální instance třídy RuntimeClass.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

Toto je podrobnost implementace.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)