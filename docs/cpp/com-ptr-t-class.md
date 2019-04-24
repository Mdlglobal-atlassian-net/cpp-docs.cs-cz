---
title: _com_ptr_t – třída
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t
helpviewer_keywords:
- _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
ms.openlocfilehash: ce19dbc5f55460bb4bdbdee17f4fbbbcc8c6fd60
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154900"
---
# <a name="comptrt-class"></a>_com_ptr_t – třída

**Microsoft Specific**

A **_com_ptr_t** objekt zapouzdřuje ukazatele rozhraní modelu COM a se nazývá "inteligentní" ukazatel. Spravuje této třídy šablony a pomocí volání funkce zrušení přidělení prostředků `IUnknown` členské funkce: `QueryInterface`, `AddRef`, a `Release`.

Inteligentní ukazatel je obvykle odkazuje v definici typedef poskytované _COM_SMARTPTR_TYPEDEF makra. Toto makro přijímá název rozhraní a IID a deklaruje jako specializaci té **_com_ptr_t** s názvem rozhraní a příponu `Ptr`. Příklad:

```cpp
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
```

deklaruje **_com_ptr_t** specializace `IMyInterfacePtr`.

Sada [funkce šablony](../cpp/relational-function-templates.md), nejsou členy této šablony třídy, podporu porovnání s inteligentním ukazatelem na pravé straně operátoru porovnání.

### <a name="construction"></a>Konstrukce

|||
|-|-|
|[_com_ptr_t](../cpp/com-ptr-t-com-ptr-t.md)|Vytvoří **_com_ptr_t** objektu.|

### <a name="low-level-operations"></a>Operace nízké úrovně

|||
|-|-|
|[AddRef](../cpp/com-ptr-t-addref.md)|Volání `AddRef` členskou funkci `IUnknown` na zapouzdřený ukazatel rozhraní.|
|[Attach](../cpp/com-ptr-t-attach.md)|Zapouzdřuje nezpracovaný ukazatel rozhraní tohoto inteligentního ukazatele typu.|
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|Vytvoří novou instanci objektu dle `CLSID` nebo `ProgID`.|
|[Detach](../cpp/com-ptr-t-detach.md)|Extrahuje a vrátí zapouzdřený ukazatel rozhraní.|
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|Připojí se k existující instanci objektu dle `CLSID` nebo `ProgID`.|
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|Vrátí zapouzdřený ukazatel rozhraní.|
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|Volání `QueryInterface` členskou funkci `IUnknown` na zapouzdřený ukazatel rozhraní.|
|[Vydaná verze](../cpp/com-ptr-t-release.md)|Volání `Release` členskou funkci `IUnknown` na zapouzdřený ukazatel rozhraní.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](../cpp/com-ptr-t-operator-equal.md)|Přiřadí novou hodnotu do existujícího **_com_ptr_t** objektu.|
|[operátory ==,! =, \<, >, \<=, > =](../cpp/com-ptr-t-relational-operators.md)|Porovná objekt inteligentního ukazatele k jiným inteligentním ukazatelem, nezpracovaný ukazatel rozhraní, nebo hodnota NULL.|
|[– Extraktory](../cpp/com-ptr-t-extractors.md)|Extrahuje zapouzdřený ukazatel rozhraní COM.|

**Specifické pro END Microsoft**

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<comip.h >

**Lib:** comsuppw.lib nebo comsuppwd.lib (viz [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Další informace)

## <a name="see-also"></a>Viz také:

[Třídy podpory kompilátoru COM](../cpp/compiler-com-support-classes.md)