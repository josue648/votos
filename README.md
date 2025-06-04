<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registro de Cuenta - Sistema Electoral</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap" rel="stylesheet">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.7.2/font/bootstrap-icons.css" rel="stylesheet">
    <style>
        :root {
            --primary-color: #1a237e;
            --secondary-color: #c62828;
            --accent-color: #ffd700;
        }

        body {
            background: linear-gradient(135deg, #f5f5f5 0%, #e0e0e0 100%);
            font-family: 'Roboto', sans-serif;
            min-height: 100vh;
            padding: 20px 0;
        }

        .registration-form {
            max-width: 600px;
            margin: 30px auto;
            padding: 40px;
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.15);
            border: 2px solid var(--primary-color);
            position: relative;
            overflow: hidden;
        }

        .registration-form::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 5px;
            background: linear-gradient(90deg, var(--primary-color), var(--secondary-color), var(--accent-color));
        }

        .form-title {
            text-align: center;
            color: var(--primary-color);
            margin-bottom: 35px;
            font-weight: 700;
            font-size: 2.2rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            position: relative;
            padding-bottom: 15px;
        }

        .form-title::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 3px;
            background: var(--secondary-color);
        }

        .form-label {
            font-weight: 500;
            color: var(--primary-color);
            margin-bottom: 8px;
        }

        .form-control {
            border: 2px solid #e0e0e0;
            padding: 12px;
            border-radius: 8px;
            transition: all 0.3s ease;
        }

        .form-control:focus {
            border-color: var(--primary-color);
            box-shadow: 0 0 0 0.2rem rgba(26, 35, 126, 0.15);
        }

        .form-select {
            border: 2px solid #e0e0e0;
            padding: 12px;
            border-radius: 8px;
        }

        .btn-register {
            background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
            border: none;
            width: 100%;
            padding: 15px;
            font-size: 18px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 1px;
            border-radius: 8px;
            margin-top: 20px;
            transition: all 0.3s ease;
        }

        .btn-register:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            background: linear-gradient(45deg, var(--secondary-color), var(--primary-color));
        }

        .form-check-input:checked {
            background-color: var(--primary-color);
            border-color: var(--primary-color);
        }

        .form-check-label {
            color: #555;
        }

        .mb-3 {
            margin-bottom: 25px !important;
        }

        /* Animación para los campos del formulario */
        .form-control, .form-select {
            animation: fadeIn 0.5s ease-in-out;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Estilo para el mensaje de éxito */
        .alert-success {
            background-color: #d4edda;
            border-color: #c3e6cb;
            color: #155724;
            padding: 15px;
            border-radius: 8px;
            margin-top: 20px;
            display: none;
        }

        .card {
            transition: transform 0.3s ease;
            border: 2px solid var(--primary-color);
        }
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }
        .card-img-top {
            height: 200px;
            object-fit: cover;
        }
        .modal-lg {
            max-width: 900px;
        }

        /* Estilos adicionales para los botones de mostrar/ocultar contraseña */
        .input-group .btn-outline-secondary {
            border-color: #ced4da;
            color: #6c757d;
        }
        
        .input-group .btn-outline-secondary:hover {
            background-color: #e9ecef;
            color: #495057;
        }
        
        .input-group .btn-outline-secondary:focus {
            box-shadow: none;
        }
        
        .bi {
            font-size: 1.1rem;
        }

        /* Estilos adicionales para los botones de votación */
        .votar-btn {
            transition: all 0.3s ease;
        }
        
        .votar-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }

        .bi-check-circle-fill {
            animation: scaleIn 0.5s ease-out;
        }

        @keyframes scaleIn {
            from {
                transform: scale(0);
                opacity: 0;
            }
            to {
                transform: scale(1);
                opacity: 1;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="registration-form">
            <h2 class="form-title">Registro de Cuenta Electoral</h2>
            <form id="registrationForm">
                <div class="mb-3">
                    <label for="nombre" class="form-label">Nombre</label>
                    <input type="text" class="form-control" id="nombre" required>
                </div>
                <div class="mb-3">
                    <label for="apellido" class="form-label">Apellido</label>
                    <input type="text" class="form-control" id="apellido" required>
                </div>
                <div class="mb-3">
                    <label for="email" class="form-label">Correo Electrónico</label>
                    <input type="email" class="form-control" id="email" required>
                </div>
                <div class="mb-3">
                    <label for="telefono" class="form-label">Teléfono</label>
                    <input type="tel" class="form-control" id="telefono" placeholder="+591 XXXXXXXX" required>
                </div>
                <div class="mb-3">
                    <label for="departamento" class="form-label">Departamento</label>
                    <select class="form-select" id="departamento" required>
                        <option value="">Seleccione su departamento</option>
                        <option value="LP">La Paz</option>
                        <option value="SC">Santa Cruz</option>
                        <option value="CB">Cochabamba</option>
                        <option value="OR">Oruro</option>
                        <option value="PT">Potosí</option>
                        <option value="CH">Chuquisaca</option>
                        <option value="TJ">Tarija</option>
                        <option value="BN">Beni</option>
                        <option value="PD">Pando</option>
                    </select>
                </div>
                <div class="mb-3">
                    <label for="fechaNacimiento" class="form-label">Fecha de Nacimiento</label>
                    <input type="date" class="form-control" id="fechaNacimiento" required>
                </div>
                <div class="mb-3">
                    <label for="fechaVotacion" class="form-label">Fecha de Votación</label>
                    <input type="date" class="form-control" id="fechaVotacion" required>
                </div>
                <div class="mb-3">
                    <label for="password" class="form-label">Contraseña</label>
                    <div class="input-group">
                        <input type="password" class="form-control" id="password" required>
                        <button class="btn btn-outline-secondary" type="button" id="togglePassword">
                            <i class="bi bi-eye"></i>
                        </button>
                    </div>
                </div>
                <div class="mb-3">
                    <label for="confirmPassword" class="form-label">Confirmar Contraseña</label>
                    <div class="input-group">
                        <input type="password" class="form-control" id="confirmPassword" required>
                        <button class="btn btn-outline-secondary" type="button" id="toggleConfirmPassword">
                            <i class="bi bi-eye"></i>
                        </button>
                    </div>
                </div>
                <div class="mb-3 form-check">
                    <input type="checkbox" class="form-check-input" id="terminos" required>
                    <label class="form-check-label" for="terminos">Acepto los términos y condiciones</label>
                </div>
                <button type="submit" class="btn btn-primary btn-register">Registrarse</button>
                <div class="text-center mt-3">
                    <a href="#" class="text-decoration-none" id="recuperarPassword">¿Olvidaste tu contraseña?</a>
                </div>
            </form>
        </div>
    </div>

    <!-- Modal de Recuperación de Contraseña -->
    <div class="modal fade" id="recuperarPasswordModal" tabindex="-1" aria-labelledby="recuperarPasswordModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="recuperarPasswordModalLabel">Recuperar Contraseña</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <form id="recuperarPasswordForm">
                        <div class="mb-3">
                            <label for="emailRecuperacion" class="form-label">Correo Electrónico</label>
                            <input type="email" class="form-control" id="emailRecuperacion" required>
                        </div>
                        <div class="mb-3">
                            <label for="dniRecuperacion" class="form-label">DNI</label>
                            <input type="text" class="form-control" id="dniRecuperacion" required>
                        </div>
                        <button type="submit" class="btn btn-primary w-100">Enviar Solicitud</button>
                    </form>
                </div>
            </div>
        </div>
    </div>

    <!-- Modal de Candidatos -->
    <div class="modal fade" id="candidatosModal" tabindex="-1" aria-labelledby="candidatosModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-lg">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="candidatosModalLabel">Candidatos Presidenciales</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <div class="row">
                        <div class="col-md-4 mb-4">
                            <div class="card h-100">
                                <img src="img\images (3).jpeg" class="card-img-top" alt="Candidato 1">
                                <div class="card-body">
                                    <h5 class="card-title">furion</h5>
                                    <p class="card-text">Partido Democrático</p>
                                    <ul class="list-unstyled">

                                    </ul>
                                    <button class="btn btn-primary w-100 mb-2">Ver más detalles</button>
                                    <button class="btn btn-success w-100">Votar</button>
                                </div>
                            </div>
                        </div>
                        <div class="col-md-4 mb-4">
                            <div class="card h-100">
                                <img src="img\images (2).jpeg" class="card-img-top" alt="Candidato 2">
                                <div class="card-body">
                                    <h5 class="card-title">grommash</h5>
                                    <p class="card-text">Partido Progresista</p>
                                    <ul class="list-unstyled">

                                    </ul>
                                    <button class="btn btn-primary w-100 mb-2">Ver más detalles</button>
                                    <button class="btn btn-success w-100">Votar</button>
                                </div>
                            </div>
                        </div>
                        <div class="col-md-4 mb-4">
                            <div class="card h-100">
                                <img src="img\images (1).jpeg" class="card-img-top" alt="Candidato 3">
                                <div class="card-body">
                                    <h5 class="card-title">thrall</h5>
                                    <p class="card-text">Partido Unidad Nacional</p>
                                    <ul class="list-unstyled">

                                    </ul>
                                    <button class="btn btn-primary w-100 mb-2">Ver más detalles</button>
                                    <button class="btn btn-success w-100">Votar</button>
                                </div>
                            </div>
                        </div>
                        <div class="col-md-4 mb-4">
                            <div class="card h-100">
                                <img src="img\Varian_Wrynn2.webp" class="card-img-top" alt="Candidato 4">
                                <div class="card-body">
                                    <h5 class="card-title">varian</h5>
                                    <p class="card-text">Partido Verde</p>
                                    <ul class="list-unstyled">

                                    </ul>
                                    <button class="btn btn-primary w-100 mb-2">Ver más detalles</button>
                                    <button class="btn btn-success w-100">Votar</button>
                                </div>
                            </div>
                        </div>
                        <div class="col-md-4 mb-4">
                            <div class="card h-100">
                                <img src="img\Illidan_antes_de_la_Metamorfosis.webp" class="card-img-top" alt="Candidato 5">
                                <div class="card-body">
                                    <h5 class="card-title">illidan</h5>
                                    <p class="card-text">Partido Laboral</p>
                                    <ul class="list-unstyled">

                                    </ul>
                                    <button class="btn btn-primary w-100 mb-2">Ver más detalles</button>
                                    <button class="btn btn-success w-100">Votar</button>
                                </div>
                            </div>
                        </div>
                        <div class="col-md-4 mb-4">
                            <div class="card h-100">
                                <img src="img\images.jpeg" class="card-img-top" alt="Candidato 6">
                                <div class="card-body">
                                    <h5 class="card-title">arthas</h5>
                                    <p class="card-text">Partido Innovación</p>
                                    <ul class="list-unstyled">

                                    </ul>
                                    <button class="btn btn-primary w-100 mb-2">Ver más detalles</button>
                                    <button class="btn btn-success w-100">Votar</button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Modal de Estadísticas -->
    <div class="modal fade" id="estadisticasModal" tabindex="-1" aria-labelledby="estadisticasModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="estadisticasModalLabel">Votos a Favor</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <div class="card">
                        <div class="card-body">
                            <canvas id="votosChart"></canvas>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Modal de Confirmación de Voto -->
    <div class="modal fade" id="confirmacionVotoModal" tabindex="-1" aria-labelledby="confirmacionVotoModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="confirmacionVotoModalLabel">Confirmar Voto</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <p>¿Está seguro que desea votar por <span id="nombreCandidato"></span>?</p>
                    <p class="text-muted">Esta acción no se puede deshacer.</p>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cancelar</button>
                    <button type="button" class="btn btn-success" id="confirmarVoto">Confirmar Voto</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Modal de Agradecimiento -->
    <div class="modal fade" id="agradecimientoModal" tabindex="-1" aria-labelledby="agradecimientoModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="agradecimientoModalLabel">¡Gracias por su voto!</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body text-center">
                    <i class="bi bi-check-circle-fill text-success" style="font-size: 4rem;"></i>
                    <p class="mt-3">Su voto ha sido registrado exitosamente.</p>
                    <p class="text-muted">Gracias por participar en el proceso electoral.</p>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-primary" data-bs-dismiss="modal">Cerrar</button>
                </div>
            </div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script>
        document.getElementById('registrationForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const password = document.getElementById('password').value;
            const confirmPassword = document.getElementById('confirmPassword').value;
            
            if (password !== confirmPassword) {
                alert('Las contraseñas no coinciden');
                return;
            }
            
            // Mostrar modal de candidatos después del registro exitoso
            const candidatosModal = new bootstrap.Modal(document.getElementById('candidatosModal'));
            candidatosModal.show();
        });

        // Funcionalidad de recuperación de contraseña
        const recuperarPasswordLink = document.getElementById('recuperarPassword');
        const recuperarPasswordModal = new bootstrap.Modal(document.getElementById('recuperarPasswordModal'));

        recuperarPasswordLink.addEventListener('click', function(e) {
            e.preventDefault();
            recuperarPasswordModal.show();
        });

        document.getElementById('recuperarPasswordForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const email = document.getElementById('emailRecuperacion').value;
            const dni = document.getElementById('dniRecuperacion').value;

            alert('Se ha enviado un enlace de recuperación a tu correo electrónico');
            recuperarPasswordModal.hide();
        });

        // Función para mostrar estadísticas
        function mostrarEstadisticas(candidatoId) {
            const estadisticasModal = new bootstrap.Modal(document.getElementById('estadisticasModal'));
            estadisticasModal.show();

            // Datos para la gráfica de votos
            const votosData = {
                labels: ['Votos a Favor', 'Votos en Contra'],
                datasets: [{
                    data: [65, 35],
                    backgroundColor: [
                        'rgba(75, 192, 192, 0.8)',
                        'rgba(255, 99, 132, 0.8)'
                    ]
                }]
            };

            // Configuración de la gráfica
            const configVotos = {
                type: 'pie',
                data: votosData,
                options: {
                    responsive: true,
                    plugins: {
                        legend: {
                            position: 'bottom'
                        }
                    }
                }
            };

            // Crear la gráfica
            new Chart(document.getElementById('votosChart'), configVotos);
        }

        // Modificar los botones de los candidatos para mostrar estadísticas
        document.querySelectorAll('.card .btn-primary').forEach((button, index) => {
            button.addEventListener('click', () => mostrarEstadisticas(index + 1));
        });

        // Función para mostrar/ocultar contraseña
        function togglePasswordVisibility(inputId, buttonId) {
            const input = document.getElementById(inputId);
            const button = document.getElementById(buttonId);
            
            button.addEventListener('click', function() {
                const type = input.getAttribute('type') === 'password' ? 'text' : 'password';
                input.setAttribute('type', type);
                
                // Cambiar el ícono
                const icon = button.querySelector('i');
                icon.classList.toggle('bi-eye');
                icon.classList.toggle('bi-eye-slash');
            });
        }

        // Inicializar la funcionalidad para ambos campos de contraseña
        togglePasswordVisibility('password', 'togglePassword');
        togglePasswordVisibility('confirmPassword', 'toggleConfirmPassword');

        // Funcionalidad de votación
        function confirmarVoto(candidato) {
            const confirmacionVotoModal = new bootstrap.Modal(document.getElementById('confirmacionVotoModal'));
            
            // Mostrar modal de confirmación
            document.getElementById('nombreCandidato').textContent = candidato;
            confirmacionVotoModal.show();
            
            // Manejar la confirmación del voto
            document.getElementById('confirmarVoto').onclick = function() {
                confirmacionVotoModal.hide();
                // Redirigir a la página de agradecimiento
                window.location.href = 'gracias.html';
            };
        }

        // Actualizar los botones de votar
        document.querySelectorAll('.btn-success').forEach(button => {
            const candidato = button.closest('.card').querySelector('.card-title').textContent;
            button.onclick = () => confirmarVoto(candidato);
        });
    </script>
</body>
</html>

