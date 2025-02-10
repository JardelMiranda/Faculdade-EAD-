# Faculdade-EAD-
Gerenciamento de um banco de dados para uma faculdade CREATE database FaculdadeEAD;

USE faculdadeead;

CREATE TABLE aluno (
  id_aluno INTEGER PRIMARY KEY,
  nome VARCHAR(100),
  data_nascimento DATE
);

CREATE TABLE Curso (
  id_curso INTEGER PRIMARY KEY,
  nome VARCHAR(100)
);

CREATE TABLE Professor (
  id_professor INT PRIMARY KEY,
  nome VARCHAR(100)
);

CREATE TABLE Materia (
  id_materia INT PRIMARY KEY,
  nome VARCHAR(100)
);

CREATE TABLE Nota (
  id_nota INT PRIMARY KEY,
  id_aluno INT,
  id_materia INT,
  valor DECIMAL(5,2),
  data_avaliacao DATE,
  FOREIGN KEY (id_aluno) REFERENCES aluno(id_aluno),
  FOREIGN KEY (id_materia) REFERENCES Materia(id_materia)
);

CREATE TABLE Matricula (
  id_aluno INT,
  id_curso INT,
  data_matricula DATE,
  PRIMARY KEY (id_aluno, id_curso),
  FOREIGN KEY (id_aluno) REFERENCES aluno(id_aluno),
  FOREIGN KEY (id_curso) REFERENCES Curso(id_curso)
);

CREATE TABLE Aluno_Materia (
  id_aluno INT,
  id_materia INT,
  data_inscricao DATE,
  PRIMARY KEY (id_aluno, id_materia),
  FOREIGN KEY (id_aluno) REFERENCES aluno(id_aluno),
  FOREIGN KEY (id_materia) REFERENCES Materia(id_materia)
);

CREATE TABLE Professor_Materia (
  id_professor INT,
  id_materia INT,
  data_inicio DATE,
  PRIMARY KEY (id_professor, id_materia),
  FOREIGN KEY (id_professor) REFERENCES Professor(id_professor),
  FOREIGN KEY (id_materia) REFERENCES Materia(id_materia)
);  

