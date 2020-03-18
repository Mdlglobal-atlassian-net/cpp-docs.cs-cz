---
title: CCustomCommand (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidercommand
- ccustomcommand
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
- CCustomCommand class in CustomRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
ms.openlocfilehash: 61bd60b63490303c65729843c3c0351a570a8056
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444149"
---
# <a name="ccustomcommand-customrsh"></a>CCustomCommand (CustomRS.H)

Třída `CCustomCommand` je implementací objektu příkazu poskytovatele. Poskytuje implementaci pro rozhraní `IAccessor`, `ICommandText`a `ICommandProperties`. Rozhraní `IAccessor` je stejné jako v sadě řádků. Objekt Command používá přistupující objekt k určení vazeb pro parametry. Objekt sady řádků je používá k určení vazeb pro výstupní sloupce. Rozhraní `ICommandText` je vhodným způsobem, jak zadat příkaz jako textový. Tento příklad používá rozhraní `ICommandText` později při přidání vlastního kódu; přepíše také metodu `ICommand::Execute`. Rozhraní `ICommandProperties` zpracovává všechny vlastnosti pro příkaz a objekty sady řádků.

```cpp
// CCustomCommand
class ATL_NO_VTABLE CCustomCommand :
class ATL_NO_VTABLE CCustomCommand :
   public CComObjectRootEx<CComSingleThreadModel>,
   public IAccessorImpl<CCustomCommand>,
   public ICommandTextImpl<CCustomCommand>,
   public ICommandPropertiesImpl<CCustomCommand>,
   public IObjectWithSiteImpl<CCustomCommand>,
   public IConvertTypeImpl<CCustomCommand>,
   public IColumnsInfoImpl<CCustomCommand>
```

Rozhraní `IAccessor` spravuje všechny vazby používané v příkazech a sadách řádků. Příjemce volá `IAccessor::CreateAccessor` s polem `DBBINDING` struktury. Každá struktura `DBBINDING` obsahuje informace o tom, jak by měly být zpracovány vazby sloupců (například typ a délka). Poskytovatel obdrží struktury a poté určí, jak se mají data přenést a zda jsou potřebné převody. Rozhraní `IAccessor` se používá v objektu Command ke zpracování libovolných parametrů v příkazu.

Objekt příkazu také poskytuje implementaci `IColumnsInfo`. OLE DB vyžaduje rozhraní `IColumnsInfo`. Rozhraní umožňuje příjemci načíst informace o parametrech z příkazu. Objekt sady řádků používá rozhraní `IColumnsInfo` k vrácení informací o výstupních sloupcích poskytovateli.

Zprostředkovatel také obsahuje rozhraní s názvem `IObjectWithSite`. Rozhraní `IObjectWithSite` bylo implementováno v knihovně ATL 2,0 a umožňuje implementátorovi předat informace o sobě samotnému objektu. Objekt Command používá informace o `IObjectWithSite` k oznámení libovolným generovaným objektům sady řádků, o tom, kdo je vytvořil.

## <a name="see-also"></a>Viz také

[Soubory generované průvodcem zprostředkovatele](../../data/oledb/provider-wizard-generated-files.md)