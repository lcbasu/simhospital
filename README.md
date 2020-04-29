# Simulated Hospital



[TOC]

*Simulated Hospital* is a tool that generates realistic and configurable
hospital patient data in
[HL7v2 format](https://www.hl7.org/implement/standards/product_brief.cfm?product_id=185).

Disclaimer: This is not an officially supported Google product.

## Overview

A hospital's Electronic Health Record (EHR) system contains patients' health
information. EHRs use messages to communicate clinical actions like the
admission of a patient, ordering a blood test, or getting test results. This
flow of messages describes the lifetime of a patient's stay in a hospital.

Most EHRs use a message format called
[HL7v2](https://www.hl7.org/implement/standards/product_brief.cfm?product_id=185),
which is ugly and tedious to type. Simulated Hospital generates messages in
HL7v2 format from sequences of clinical actions. The generated HL7v2 messages
can be sent to an
[MLLP](https://www.hl7.org/implement/standards/product_brief.cfm?product_id=55)
host, saved to a txt file, or printed to the console.

Simulated Hospital helps developers build and test clinical apps that work with
HL7v2 by making it easy to generate HL7v2 messages that reproduce realistic
situations in clinical settings. Simulated Hospital uses *pathways* to model
clinical actions and events that occur to patients in hospitals.

## Pathways

A pathway is a sequence of clinicial actions or events that describe the
lifetime of a patient's stay in a hospital. An example of a simple pathway could
be: the patient is admitted, a doctor orders an X-ray, the X-ray is taken, and
the patient is discharged. Each action typically generates one or more HL7v2
messages.

Simulated Hospital runs pathways. You can configure Simulated Hospital to run
the pathways that you want, including how frequently to run each one. The
application includes a few built-in pathways (see the folder
_"config/pathways"_) but most people will want to write their own.

Pathways are written using YAML or JSON and are human readable. The events are
defined with words that are common in clinical settings such as "admission",
"discharge", etc., and utility actions such as time delays.

## Next steps

*   Get started by [installing & running SH](./docs/get-started).

*   [Write pathways](./docs/write-pathways) to create patients with specific
    conditions, for instance, a patient with appendicitis that has sets of Vital
    Signs taken periodically.

*   Change the default behavior of Simulated Hospital using
    [command-line arguments](./docs/arguments), including:

    *   What pathways Simulated Hospital runs and their distribution, i.e., what
        pathways should run more frequently than others.
    *   What specific values to set for some fields in the HL7v2 messages in
        order to comply, or not, with the values in the HL7v2 standard. For
        instance, you can configure what should be set as the Sending Facility
        in the generated messages, or what keyword to use to represent that a
        set of laboratory results is amended.
    *   The demographics of the patients that are generated: names, surnames,
        ethnicity, etc. For instance, you can configure how many patients will
        have middle names, or what is the probability that a patient will have
        pre-existing allergies.

*   Control a running instance Simulated Hospital using its
    [Dashboard](./docs/dashboard) [(screenshot)](./docs/images/control-panel.png). Using
    the dashboard, you can do the following:

    *   Change the message-sending rate of a self-running simulation.
    *   Start an ad-hoc pathway or send an HL7v2 message.

*   [Extend Simulated Hospital](./docs/extend-sh) with advanced functionality using
    source code. For instance, you can change the format of the identifiers that
    Simulated Hospital generates, or create your own behavior for some events.