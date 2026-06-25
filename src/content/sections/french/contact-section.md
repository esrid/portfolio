---
enable: true
badge: "contact"
title: "Un projet en tête ? <br /> Parlons-en."
description: "30 minutes pour identifier ce qu'on peut automatiser chez vous — sans engagement."
image: "https://images.unsplash.com/photo-1497366216548-37526070297c?w=800&q=80"
imageAlt: "Open space moderne"
characterImage: ""
characterImageAlt: ""

form:
  emailSubject: "Nouveau message depuis bureau-mq.com"
  submitButton:
    enable: true
    label: "Envoyer"
  inputs:
    - label: "Nom"
      placeholder: "Votre nom *"
      name: "Nom"
      required: true
      halfWidth: true
      defaultValue: ""
    - label: "Email"
      placeholder: "Votre email *"
      name: "Email"
      required: true
      type: "email"
      halfWidth: true
      defaultValue: ""
    - label: "Entreprise"
      placeholder: "Votre entreprise"
      name: "Entreprise"
      required: false
      type: "text"
      halfWidth: false
      defaultValue: ""
    - label: "Message"
      tag: "textarea"
      placeholder: "Décrivez votre besoin en quelques lignes"
      name: "Message"
      required: true
      halfWidth: false
      rows: "4"
      defaultValue: ""
    - note: success
      parentClass: "hidden text-sm message success"
      content: "Message reçu ! Je vous réponds sous 24h."
    - note: deprecated
      parentClass: "hidden text-sm message error"
      content: "Une erreur s'est produite. Essayez à nouveau."
---
