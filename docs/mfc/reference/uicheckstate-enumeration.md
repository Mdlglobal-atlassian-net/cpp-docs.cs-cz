---
title: Uicheckstate – výčet | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/03/2017
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- afxwinforms/uicheckstate
dev_langs:
- C++
helpviewer_keywords:
- uicheckstate enumeration [MFC]
ms.assetid: 2ac0098c-20e7-410c-9685-5ead5cb02b63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc09dcb36d7d1ec1abd2f51fd13b6daadd74601f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403848"
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
