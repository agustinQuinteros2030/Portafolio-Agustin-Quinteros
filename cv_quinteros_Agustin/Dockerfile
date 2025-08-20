# Etapa de build
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
COPY . .
RUN dotnet publish cv_quinteros_Agustin.csproj -c Release -o /out

# Etapa de runtime
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app
COPY --from=build /out .
# Render usa la variable PORT para asignar un puerto dinámico
ENV ASPNETCORE_URLS=http://0.0.0.0:${PORT}
CMD ["dotnet", "cv_quinteros_Agustin.dll"]
