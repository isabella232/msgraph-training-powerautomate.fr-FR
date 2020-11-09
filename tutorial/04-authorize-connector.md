---
ms.openlocfilehash: bf83723de025f3e1f6bde5b4226fc8966dff6b9a
ms.sourcegitcommit: 64947f11d367ffbebbafb700fdfdc20617275f35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "48829664"
---
<!-- markdownlint-disable MD002 MD041 -->

L’étape de configuration finale permettant de s’assurer que le connecteur est prêt à être utilisé est d’autoriser et de tester le connecteur personnalisé afin de créer une connexion mise en cache.

> [!IMPORTANT]
> Pour suivre les étapes suivantes, vous devez être connecté avec des privilèges d’administrateur.

Dans [Microsoft Power automate](https://flow.microsoft.com), accédez à l’élément de menu **données** à gauche et choisissez la page **connexions** . Sélectionnez le lien **nouvelle connexion** .

![Capture d’écran du bouton nouvelle connexion](./images/new-connection.png)

Recherchez votre connecteur personnalisé et terminez la connexion en cliquant sur le bouton plus. Connectez-vous à l’aide de votre compte Azure Active Directory de l’administrateur client Office 365.

![Capture d’écran de la liste connexions](./images/connection-sign-in.png)

Lorsque vous êtes invité à entrer les autorisations demandées, vérifiez le **consentement au nom de votre organisation** , puis choisissez **accepter** pour autoriser les autorisations.

![Capture d’écran de l’invite de consentement](./images/consent-prompt.png)

Une fois que vous avez autorisé les autorisations, une connexion est créée dans Power automate.

Le connecteur personnalisé est maintenant configuré et activé. Il peut y avoir un retard dans les autorisations appliquées et disponibles, mais le connecteur est maintenant configuré.
