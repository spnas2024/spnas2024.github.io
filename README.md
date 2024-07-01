# SP-NAS: Surgical Phase Recognition-based Navigation Adjustment System for distal gastrectomy

Surgical navigation systems enhance surgical efficiency and outcomes, especially in minimally invasive surgeries by providing 3D anatomy models from CT scans. We introduce the Surgical Phase Recognition-based Navigation Adjustment System (SP-NAS) for distal gastrectomy, which uses surgical phase recognition for workflow-based adjustments. This system eliminates the need for real-time camera adjustments and challenging registrations by defining three reference views for ten surgical phases. We employed recent action recognition models to identify surgical phases, training and evaluating them on 146 robotic distal gastrectomy cases using 6-fold cross-validation. Our system demonstrated effective phase recognition and post-processed predictions, resulting in a deployable real-time solution.

## Phase and View Visualization
### Phase
![phase_visualization](https://private-user-images.githubusercontent.com/173689526/344650384-72928e97-bdd4-4648-a05e-8efb659ba08e.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MTk4MzI0NDIsIm5iZiI6MTcxOTgzMjE0MiwicGF0aCI6Ii8xNzM2ODk1MjYvMzQ0NjUwMzg0LTcyOTI4ZTk3LWJkZDQtNDY0OC1hMDVlLThlZmI2NTliYTA4ZS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwNzAxJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDcwMVQxMTA5MDJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0zM2ZkY2ZjNjM1MDRiOGY1YjQ1Nzg2N2MwM2YyZjg2MTA5ODNmMmFjODhmNDAxY2MwYmM2NGM4YzgyYjhiN2ZkJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.sc3BT3dHFLvugUyos5ogF_pf7aeX4d8mnEGO6-KQRLg)

### View
![View_visualization](https://private-user-images.githubusercontent.com/173689526/344650372-63b3e476-b995-4818-b958-6c47d411a313.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MTk4MzI0NDIsIm5iZiI6MTcxOTgzMjE0MiwicGF0aCI6Ii8xNzM2ODk1MjYvMzQ0NjUwMzcyLTYzYjNlNDc2LWI5OTUtNDgxOC1iOTU4LTZjNDdkNDExYTMxMy5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwNzAxJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDcwMVQxMTA5MDJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT05NjJjYmY4ZWUwY2ZjMmE5N2JhYmZjNThmZjhmYjEwZjdmNTZiOWJiODhmZWQ4NWE0ZDc1NDNmNmM4NzFkZDkwJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.how0YatoslRHHxAV5Uu1jVpLl3QJ9-QEgg5sW0mcvgE)

## [Demonstraction Video](https://youtu.be/-5XcyDxla4g?si=HiImo0sJx8Ds8-Y3)
[![demonstraction_video](https://private-user-images.githubusercontent.com/173689526/344650398-f6eb9a03-e8ac-4066-9e51-02350d654080.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MTk4MzI3NjIsIm5iZiI6MTcxOTgzMjQ2MiwicGF0aCI6Ii8xNzM2ODk1MjYvMzQ0NjUwMzk4LWY2ZWI5YTAzLWU4YWMtNDA2Ni05ZTUxLTAyMzUwZDY1NDA4MC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwNzAxJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDcwMVQxMTE0MjJaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0zMjZiOTFmZDBhMmQwYTU0Zjc3ODNmZThlYTAzMmUzY2E0OGM1N2FlM2M5MDc0YzBlNWQ2ODdhNWUxYzYzMDBmJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9._qTizm19O33RnRx-N9An8eL62EmQmrjUQn60Yk112bU)](https://youtu.be/-5XcyDxla4g?si=HiImo0sJx8Ds8-Y3)
