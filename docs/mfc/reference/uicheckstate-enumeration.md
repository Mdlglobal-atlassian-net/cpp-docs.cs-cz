---
title: UICheckState – výčet
ms.date: 04/03/2017
f1_keywords:
- afxwinforms/uicheckstate
helpviewer_keywords:
- uicheckstate enumeration [MFC]
ms.assetid: 2ac0098c-20e7-410c-9685-5ead5cb02b63
ms.openlocfilehash: 1411e9b7cb088c063e17cc7c59871e5f0b83ad9c
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51692499"
---
# <a name="uicheckstate-enumeration"></a>UICheckState – výčet

Popisuje stavu zaškrtnutí položky uživatelského rozhraní pro příkaz.

### <a name="syntax"></a>Syntaxe

```
public enum class
{
   [DefaultValue(typeid<Microsoft::VisualC::MFC::UICheckState>, "Checked")]
   Unchecked,
   Checked,
   Indeterminate
};
```

### <a name="remarks"></a>Poznámky

[ICommandUI::Check](icommandui-interface.md#check) tyto hodnoty používá k popisu stavu položku uživatelského rozhraní.
Další informace o používání formulářů Windows, naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms.h (definované v sestavení atlmfc\lib\mfcmifc80.dll)
