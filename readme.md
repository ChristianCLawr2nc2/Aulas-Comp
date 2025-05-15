# Estudo das aulas de Computação do Módulo #


Respondendo a perunta
*Explique com suas palavras o funcionamento do models, controller e fale sobre endpoints no projeto.*

**Models:**
São os que se comunicam com o banco de dados diretamente tendo acesso a todas as informações presentes nele, também podendo escrever dentro dos models com a linguagem do banco de dados como SQL.
 - exemplo: 

```javascript
async findAllComCurso() {
  const query = `
    SELECT aluno.id, aluno.nome, aluno.email, curso.nome AS curso
    FROM aluno
    LEFT JOIN curso ON aluno.curso_id = curso.id
    ORDER BY aluno.id ASC
  `;
}
```
**Controllers:**
São os intermediários entre o view e o model que levam as requisições de usuários (por exemplo) para mostrar um informação do banco de dados no view ou enviar uma informação para o banco.
 - exemplo:

```javascript
exports.update = async (req, res) => {
  const { id } = req.params;
  await Aluno.update(id, req.body);
  res.redirect('/alunos');
};
```

**Endpoints:**
São como rotas API que armazenam informações de ordens para o controller enviadas do view.
 - exemplo:
```javascript
const professoresRoutes = require('./routes/professores');
app.use('/professores', professoresRoutes);
```
